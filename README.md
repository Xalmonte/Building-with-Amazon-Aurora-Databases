# Building-with-Amazon-Aurora-Databases

## Lab Objectives

1. Understand how parallel query can benefit your workload
2. Understand the benefit of parallel query for large datasets
3. Determine some of the situations that trigger parallel query


## Step by step Instructions

1. In the AWS Console, Search and choose RDS
2. On the left side, click Databases
3. On the left side, I selected Parameter groups
4. Next, I selected  the name of the parameter group that contains "dbclusterparametergroup"
5. In the Filter parameters field at the top of the table, I entered aurora_parallel_query and the parameters should be set to ON

   <img width="1431" alt="step 1" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/de11d6b5-32aa-412d-bbf8-38861ef282a4">

6. In the field parameters field, I entered aurora_disable_hash_join and the parameters should be set to 0

   <img width="1431" alt="step 2" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/55585b6a-8510-4e6b-8c71-d978e7accf75">

7. On the AWS Console, select EC2

   <img width="1431" alt="step 3" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/935c5f45-d8c1-449b-b27d-1223aefd288b">

8. Select Instances on the left side, I selected the Instance created for me by AWS and clicked on connect

   <img width="1431" alt="step 4" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/cf7fecc5-d47b-4e5a-8a66-db40460b161c">

9. I then selected Session Manager and connect

    <img width="1431" alt="step 5" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/f7645832-f49f-413f-bb1f-b0fa9da2f452">


10. Once the terminal opens, I typed the following command:

    <img width="1431" alt="step 6" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/c218d2fd-c448-481e-981f-9bcce6ae7cb6">

11. I then typed in the following command:

    <img width="1431" alt="step 7" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/a7dee00f-cccc-4fbd-b361-e690c33b2a29">

12. It prompted me for a password which I entered. Now I want to use the ontimeflights database so I typed the following command:

    <img width="1431" alt="step 8" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/75e04c4b-67a4-4388-abf7-ba62e263209b">

13. To show the tables in the database, I used the following command:

    <img width="1431" alt="step 9" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/98dc93fa-5058-4825-a4c7-6b56493601dd">

14. I now wanted to find details about the carriers table so I ran the following command:

    <img width="1431" alt="step 10" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/9540739b-15c0-4c2b-b576-8b92b909f2fa">

15. To view a sample of the data, I ran the following statement:

    <img width="1431" alt="step 11" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/a29ad71b-312f-41f5-9209-63848b9d5632">

16. To show details about the flightdata table, I ran the following statement:

    <img width="1431" alt="step 12" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/228657bc-1484-4af4-be14-45b9ca1b2c1a">


17. To show the row count for the table, I ran the following statement:

    <img width="1431" alt="step 13" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/dcfea713-73e5-449a-adb7-d4ee0d2c72ef">

18. Now to determine if the parallel query is anabled on the Instance for my session, I ran the following statement:

    <img width="1431" alt="step 14" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/936e2e1e-9c49-4b11-981a-de7d3f3369ce">

19. To disable parallel query on the Instance for my query, I ran the following statement:

<img width="1431" alt="step 15" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/536ca25f-ca5a-4ebe-af30-d04314b9b64d">

20. To confirm this, I ran the following statement:

        <img width="1431" alt="step 16" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/76374b41-2296-463e-8170-b64c27cee26e">

21. I returned to the AWS Console and searched and selected Cloudwatch

    <img width="1431" alt="step 17" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/dd8dd004-1895-412a-9e4d-7be1b9fc780f">


22. On the left side, I selected Dashboards

    <img width="1431" alt="step 18" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/da79e6c0-583e-4322-85f1-a5153cc858e0">

23. I selected the name called ontimeflights-Dashboard

    <img width="1431" alt="step 19" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/a7511c58-36a4-4b74-aa15-8cf08c987b21">


24. I scrolled to the RDS: Instance PQ Stats graph

    <img width="1431" alt="step 20" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/eed65da7-ae31-43ce-8b97-39cbb6a8ad5c">


25. After I observed it, I returned to the CommandHost terminal window. I needed to determine if the query plan will recommend parallel query so I ran the following statement:

    <img width="1431" alt="step 21" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/9677610a-addb-4b38-a588-9c2a0034f91c">

26. In the output, I added an extra column which should show NULL. I should not see using parallel query running the following statement:

    <img width="1431" alt="step 22" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/480accc3-10fd-4ccf-b6be-28f4dfaae724">

27. I then ran the following statement:

    <img width="1431" alt="step 23" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/7a0b2f4b-358a-4411-b610-4d040eb31bc9">


28. To display the current innodb_buffer_pool statistics, I ran the following statement:

    <img width="1431" alt="step 24" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/81de2741-835d-403f-9f5a-472030779e55">

29. The following statements will disable both parallel query parameters for this session and issue a complex statement:

    <img width="1431" alt="step 25" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/99784d30-b03d-4d0e-b53a-1280398eb00f">

30. To display the current innodb_buffer_pool statistics, I ran the following statements:

<img width="1431" alt="step 26" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/e1257aca-e688-492d-83d9-1a129d1675cb">

31. To see the impact of having a database cache, I ran the following statement:

    <img width="1431" alt="step 27" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/a31f5ae0-c2ee-4c84-8664-351627861907">


32. I ran the following statement without parallel query or cache:

    <img width="1431" alt="step 28" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/befcd0b1-9712-4afb-b01c-c40f4326d02c">


33. To display the current innodb_buffer_pool statistics, I ran the following statement:

    <img width="1431" alt="step 29" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/39b642b0-0e55-4ba7-9c18-91f728f864d1">


34. To determine the average flight delay, I ran the following statement:

    <img width="1431" alt="step 30" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/688d0256-597d-413f-8578-b343bac6b208">


35. To display the current innodb_buffer_pool statistics, I ran the following statement:

36. After completing the above, I returned to the Amazon Cloudwatch Management Console and searched and went to RDS

    <img width="1431" alt="step 31" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/e840af5e-44f7-4d5b-a37c-3a35c3c1c17f">


37. On the left side, click Databases and select the name of the instance with the Writer role to review the Instance class, number of vCPUs, and amount of RAM the writer has. Repeat the same steps for the instance with 
the Reader role.

<img width="1431" alt="step 32" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/e693a746-f15c-420d-87dc-621c12109f49">

38. To view the maximum concurrent parallel query sessions allowed with this instance type, I ran the following statement in the CommandHost Session Window:

<img width="1431" alt="step 33" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/142684e3-be3e-47bf-a9df-f40feeedab30">

39. To disconnect from the database server, I ran the following command:

         <img width="1431" alt="step 34" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/0d04e5f4-0db6-4c05-b1c1-14a44c15dda7">

40. Now I ran the following command:

<img width="1431" alt="step 35" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/38a4fde5-9fd4-4853-8c6e-18ce149df8a3">

41. Followed by this command:

   <img width="1431" alt="step 36" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/e83438ec-3361-4ff3-8ed7-2bcf716ae2cc">

42. Now I will use the SQL Query used by the run-pq.sh script which fetches flights where the distance is less than 1,000 miles with a carrier code of AA, UA, DL, or b6 using the following statement:

    <img width="1053" alt="step 37" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/f63a1a98-4589-4039-8ed4-ed45dc866f7f">

43. This is the output:

   <img width="1431" alt="step 38" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/4785fc9c-60cf-48b8-9a89-1ea71a160ec1">

 44. Now to test the larger instance, we will connect to it using the following statement:

     <img width="1438" alt="step 39" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/75b7682e-d2d0-4ad3-a8b6-c0726f08c075">

45. To use the ontimeflights database, I ran the following statement:

   <img width="1438" alt="step 40" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/575bc7d2-df1d-420c-85b1-77c8ec39c68c">

46.   To view the maximum concurrent parallel query sessions allowed with this Instance type, I ran the following statement:

    
<img width="1438" alt="step 41" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/6c9bb235-af81-410d-a7d7-730546829cc8">

47. To exit the database server, I ran the command: Exit; I then used the following command:

    <img width="1417" alt="step 42" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/3028d198-b5dc-41a9-b80f-8e7df9c86842">

48. The expect output shows the larger instance should roughly have the same time elapsed, since the larger number of concurrent parallel queries is supported by the larger instance allowed both queries to use the feature. (step not shown)

49. Now we head back to the AWS Console, and into CloudWatch

    
<img width="726" alt="step 43" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/0539fad4-c5ed-4f05-83f1-0b8242db202f">

50. Select Dashboards on the left side and click on the name of the ontimeflights-Dashboard Dashboard

   <img width="726" alt="step 44" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/0f9d50ed-e1b4-46ba-b4b8-8ab574b9fb23">

51. Now it's time to hover over the latest peaks on the widget RDS: Instance PQ Stats (Step not shown) and RDS: Large Instance PQ Stats

    <img width="726" alt="step 45" src="https://github.com/Xalmonte/Building-with-Amazon-Aurora-Databases/assets/169603464/3a7e991e-d649-49e9-8d69-ad8f34ca0247">

52. That concludes the lab!
