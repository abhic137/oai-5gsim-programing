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
   sudo ./program_uicc --adm <ADM_VALUE_FROM_SIM> --key 0C0A34601D4F07677303652C0462535B --opc 63bfa50ee6523365ff14c1f45f88737d --authenticate --noreadafter 
```
quectel-ue-program uicc output for 

Ensure that the values being programmed into the SIM card match the corresponding values entered in the SQL database on the CN machine. The values of primary importance are listed in the table below.

### Primary Configuration Parameters for UE, gNB, CN Parameter 	UE 	gNB 	CN
```
IMSI 	208920100001101 	MCC: 208, MNC: 92 	208920100001101
MSISDN 	00000101 		00000101
IMEI 	863305040549338 		863305040549338
Key 	0C0A34601D4F07677303652C0462535B 		0C0A34601D4F07677303652C0462535B
OPC 	63bfa50ee6523365ff14c1f45f88737d 		63bfa50ee6523365ff14c1f45f88737d
```
