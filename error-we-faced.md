1. When running the insights module pipeline, it was getting timed out as it is always in queued status and never getting processed. 
We had to use the spark pool for each of the notebooks to make the pipeline successful. It would be great if this is mentioned somewhere in the documentation.
2. Microsoft Education Insights Module Version 0.2 has been removed from the github repository with out any notice, as a result we had to use version 0.1.
3. When we trigger the insights module by using 0_main_insights in that process, it runs 2_ingest_insights after completing the landing process. In the 2_ingest_insights pipeline by default, it is using "spark3p2med" as sparkpool. Because of we have used "spark3p2sm" for the trigger Contoso module. We need to use the same for the education insights module we need to change sparkpool "spark3p2med" to "spark3p2sm". otherwise it will show the status queued while the pipeline is triggered.

Change in pipeline 2_ingest_insights

"sparkPool": {
    "referenceName": "spark3p2med",
    "type": "BigDataPoolReference"
},

to change

"sparkPool": {
    "referenceName": "spark3p2sm",
    "type": "BigDataPoolReference"
},
