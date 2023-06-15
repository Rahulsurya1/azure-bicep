# This is a basic workflow to help you get started with Actions

name: Create azure_vm in various envs
on:
  push:
    branches: dev
jobs:
  review:
    runs-on: self-hosted
    environment: review
    steps:
      - name: Checkout
        uses: actions/checkout@v3.5.2
        
      - name: create resource group
        run: az group create --name rg-01 --location eastus
 
      - name: azure view deployment changes
        run: az deployment group what-if --resource-group rg-01 --template-file iac.bicep
   
  DEV:
    runs-on: self-hosted
    environment: dev
    needs: review
    steps:
      - name: Checkout
        uses: actions/checkout@v3.5.2
        
      - name: create azure_vm in DEV ENV 
        run: az deployment group create --resource-group rg-01 --template-file iac.bicep
    
  
  QA:
    runs-on: self-hosted
    environment: qa
    needs: DEV
    steps:
      - name: Checkout
        uses: actions/checkout@v3.5.2
          
      - name: create azure_vm in DEV ENV 
        run: az deployment group create --resource-group rg-01 --template-file iac.bicep
      
 
     
     
     
          

