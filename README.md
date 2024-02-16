# oai-5gsim-programing
## Configuring the SIM Card

When using a 5G wireless modem module or a COTS handset, a SIM card will be required. If a USRP is being used as the UE, running the OAI UE softmodem, then a SIM card is not required.

The SIM card used in this reference architecture is provided by Open-Cells, and is shown below. Note that the ADM code is printed directly on the SIM card itself.

Insert the nano SIM card into the SIM card reder/writer, and plug it into the USB slot on the UE computer.

To read and program the SIM card, we use the program program_uicc from Open-Cells (https://open-cells.com/index.php/uiccsim-programing/)

We first read the existing data on the SIM by running the command below.
```
   sudo ./program_uicc --adm 1
```
quectel-ue-program uicc output for 

We then write the key and the OPC in the UICC file in the SIM card. The ADM value enables this. Run the command below to perform this operation, where ADM_VALUE_FROM_SIM is the ADM value printed directly on the SIM card itself.
```
sudo ./program_uicc --adm 0c008521 --imsi 001010000000037 --isdn 00000037 --key 6874736969202073796d4b2079650a73 --opc 504f20634f6320504f50206363500a4f -spn "idrbt" --authenticate --noreadafter 

```

```
sudo ./program_uicc --adm 0c008520 --imsi 001010000000036 --isdn 00000036 --key 6874736969202073796d4b2079650a73 --opc 504f20634f6320504f50206363500a4f -spn "idrbt" --authenticate --noreadafter 


```
![sim program](https://github.com/abhic137/oai-5gsim-programing/assets/46273637/4dfb64d6-5221-432a-8d83-dbb98c582aa5)



Basic format to write a sim
```
   sudo ./program_uicc --adm <ADM_VALUE_FROM_SIM> --key <KEY_VALUE> --opc <OPC_VALUE> --authenticate --noreadafter 
```


Ensure that the values being programmed into the SIM card match the corresponding values entered in the SQL database on the machine. 
# SQL file in the 5G core.
look for the sqldb file which is being used by the core.
you will find the .sql db file in this path
```
OAI-5G-core/docker-compose/database
```
we can find which .sql file our deployment is using over here
![sqldb](https://github.com/abhic137/oai-5gsim-programing/assets/46273637/d11f7264-e94e-4eb8-9f9d-5fd715744109)


### AMF LOGS (sims connected to the 5G core)
![sim connected](https://github.com/abhic137/oai-5gsim-programing/assets/46273637/9deff597-2e77-4baf-803e-be337daa211b)
