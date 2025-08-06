
# Validations and Transformations

### Typical API layer Interaction
- 1. Repository Layer -> deals with database interactions
- 2. Service Layer -> Have the business Logic
- 3. Controller Layer -> Handle necessary Http Request Handling by calling necessary Service Layer Methods


 -> data -> validation & transformationlayer -> controller layer

# Validation


- validations and Transformations can happen before payload is entering into the server controller layer
- why validation -> to stop from unexpected breakdown of our systems like 500 error if wrong data is entered in to database

- Types of validations 
- 1. Syntatic - email,phone,date
- 2. Semantic - FutureDate,age -> 365
- 3. Type Validation - string,boolean,custom json data type ..etc


# Transformations

 Query Paramters Example -> transform data as per necessary 
  /bookmarks?page=2&limit=20
  by default page="2" and limit="20" the data is in string by default we needed to change that to numbers so apply transformations for those

  example: Api Example email : captial or small letter, phone:+ format 

 - Api Postman example 

 ### Frontend Validation (ux) and Backend Validation
 ex: Basic Form example
- frontend validation -> for user experience for security
- backend validation -> for security
- build backend indenpendent of frontend -> strict validatin and transformation is required

