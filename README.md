Project Setup:

Created a Node.js Project with Express and MongoDB for processing and storing CVE Data.

Used MongoDB to connect to backend and performed storing and retriving of  CVE records.

Initial Logic :

Focus on the Backend Part:

./server/models/CVE.js

Created a CVESchema to store all the necessary values from the API.

The API has nested values, but I have retrived them like a flattened structure for easier process and fetching .

./server/utils/CVEAPI.js

Implemented logic to fetch paginated data from the CVE API (1000 per each page).

Processed the data under the function processData , to fetch all the important fields and their respective values after flatting the nested structure, also handled duplicates using findone 

Error Handling: 

- Handled `503` errors from the CVE API by adding a `skipCounter` variable to continue fetching data from the next index after a failure.
- Implemented logic to track how many records were successfully stored in MongoDB
- **Pagination, Filtering, and Sorting**:
    - Added a `/cves` endpoint to fetch CVEs with:
        - Pagination (`page` and `limit`).
        - Sorting ( `publishedDate` ).
        - Filtering by fields like `cveId`, `year`, `score`, and `lastModifiedDays`.
- **API Documentation with Swagger**:
    - Used `swagger-jsdoc` and `swagger-ui-express` to generate interactive documentation.
    - http://localhost:5000/api-docs/  to get the swagger documentation

Frontend Integration :

React framework was used for frontend

Displayed CVE data in a table format with features like pagination, number of records per page and sorting using Published Date .

Details View for the records on clicking over them.

Routes:

./cves : fetches paginated, sorted data,

./cves/:id : fetches single CVE by it’s cveId
![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/985e13a4-2b26-4465-9a36-9010099d1443/2901e789-a6d8-4969-a267-3497752ce24b/image.png)


