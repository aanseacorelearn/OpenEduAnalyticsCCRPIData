1. When running the insights module pipeline, it was getting timed out as it is always in queued status and never getting processed. 
We had to use the spark pool for each of the notebooks to make the pipeline successful. It would be great if this is mentioned somewhere in the documentation.
2. Microsoft Education Insights Module Version 0.2 has been removed from the github repository with out any notice, as a result we had to use version 0.1.

\n
AttributeError                            Traceback (most recent call last)\n/tmp/ipykernel_7698/3877019711.py in <module>
\n      1 metadata = oea.get_metadata_from_url('https://raw.githubusercontent.com/aanseacorelearn/education_insight/main/test_data/metadata.csv')
\n----> 
2 ingest_insights_dataset('stage1/Transactional/M365/v' + version)
\n\n/tmp/ipykernel_7698/781238696.py in ingest_insights_dataset(tables_source)
\n     22                 oea.ingest(entity_path, '_c3', options)
\n     23             elif item == 'graduationRatesbySubgroup':
\n---> 24                 if(should_ingest(entity_path)):
\n     25                     oea.ingest(entity_path, '_c5', options)
\n     26             else:\n\n/tmp/ipykernel_7698/781238696.py in should_ingest(entity_path)
\n      7     if batch_type == 'snapshot' or batch_type=='additive': source_url = f'{source_url}/{oea.get_latest_folder(source_url)}'
\n      8 
\n----> 9     return oea.get_folder_size(source_url) > 0
\n     10 
\n     11 # 2) this step refines the data through the use of metadata (this is where the pseudonymization of the data occurs).
\n
\n AttributeError: 'OEA' object has no attribute 'get_folder_size'




{
    "errorCode": "BadRequest",
    "message": "Operation on target get list of entities failed: ADLS Gen2 operation failed for: Operation returned an invalid status code 'NotFound'. Account: 'stoeaaanseacoreoeav09'. FileSystem: 'oea'. Path: 'dev/stage2/Refined/M365/v1.4.0/general'. ErrorCode: 'PathNotFound'. Message: 'The specified path does not exist.'. RequestId: 'ea5b55cd-001f-0009-652f-809abc000000'. TimeStamp: 'Sat, 06 May 2023 15:26:50 GMT'.",
    "failureType": "UserError",
    "target": "create_sql_db_for_general",
    "details": ""
}


{
    "errorCode": "BadRequest",
    "message": "Operation on target get list of entities failed: ADLS Gen2 operation failed for: Operation returned an invalid status code 'NotFound'. Account: 'stoeaaanseacoreoeav09'. FileSystem: 'oea'. Path: 'dev/stage2/Refined/M365/v1.4.0/sensitive'. ErrorCode: 'PathNotFound'. Message: 'The specified path does not exist.'. RequestId: '98f09414-d01f-009c-0c2f-807209000000'. TimeStamp: 'Sat, 06 May 2023 15:27:00 GMT'.",
    "failureType": "UserError",
    "target": "create_sql_db_for_sensitive",
    "details": ""
}
