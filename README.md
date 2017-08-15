# glacierd
Download AWS Glacier archive files using CLI for Windows
========================================================

Dependencies:
=============
- Windows OS
- .NET 4.5
- AWS CLI tool https://aws.amazon.com/cli/ (for windows/linux it doesn't matter)

How it works?
=============
1. Download two file (from: https://github.com/asafs133/glacierd/releases):
   - GlacierDSetup.msi
   - setup.exe

2. Complete the setup wizard.

3. Default folder location: "C:\Program Files (x86)\Glacier\GlacierD\"

4. Execute glacierd.exe file in CMD, add arguments.
   * accessKey secretKey region destinationPath vaultName jsonFile
   * Example command: glacierd.exe accessKey secretKey EUWest1 c:\myDownloads\ vaultName c:\jsonFile.json

5. You may use "glacierd.exe --help" for arguments.

- accessKey: AWS accessKey
- secretKey: AWS secretKey
- region: The region who holds the vault
- destinationPath: The folder to which I want to download the files
- vaultName: AWS vaultName
- jsonFile: Output json file from AWS CLI (For more information about how to generate inventory json file, see below)

How to generate inventory json file?
====================================
aws glacier initiate-job --account-id - --vault-name the_name_of_glacierVault --job-parameters '{"Type": "inventory-retrieval"}'

aws glacier get-job-output --account-id - --vault-name the_name_of_glacierVault --job-id the_jobID_which_recieved_from_the_initiate-job_command /tmp/inventory_list.json
