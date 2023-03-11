# Database
You can use this docker-compose file ('compose' yaml source file) to create a local mssql db for testing things when you don't want to connect to a shared environment.

## Setup
1. Install docker for whatever operating system you use (https://docs.docker.com/get-docker/)

## Usage
1. Copy the .env.example file and re-name it to .env
2. Run `echo ${home}` to get the local home directory
    -  Update `HOME` variable in the .env file to match the output of the `echo ${HOME}` command
4. Choose a password and replace the variable MSSQL_ROOT_PASSWORD in the .env file
5. Allow scripts to run
    - For Windows - Open powershell as an administrator, and run the following command: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`
    - Linux/Mac - make the shell script executable with the following command `chmod +x start-db.sh`
6. Generate the container by running one of the following scripts:
* Windows
  ```
  start-db.ps1
  ```
* Mac/Linux
  ```
  start-db.sh
  ```

## Connecting to the DB
- Connect to the DB using your favorite app like AzureDataStudio or something else
- Example connection string for connecting without initial catalog
```json
    "Default": "Server=localhost,1456;Persist Security Info=False;User ID=sa;Password=SomeSecurePassword123!;MultipleActiveResultSets=False;TrustServerCertificate=True;Connection Timeout=30;",
```
- after creating the initial DB and running migrations be sure to add the initial catalog to the connection string
```json
"Default": "Server=localhost,1456;Initial Catalog=HangFireSqlPOC;Persist Security Info=False;User ID=sa;Password=SomeSecurePassword123!;MultipleActiveResultSets=False;TrustServerCertificate=True;Connection Timeout=30;"
```