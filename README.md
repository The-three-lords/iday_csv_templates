[rainbow]: media/rainbow.png "VSCode with rainbow"
[open]: media/Open.png "Open with VSCode"
[vscode]: media/VSCodePrepared.png "VsCode Prepared"
[csvlint]: media/csvlint.png "CSV LINT"
[badcsvlint]: media/badcsvlint.png "CSV LINT with error"

<p align="center">
<br/>
<br/>
<br/>
   <img src="media/Logo_StartUB.png" width="330"/>
<br/>
<br/>
</p>

![GitHub Contributors Image](https://contrib.rocks/image?repo=The-three-lords/iday_csv_templates)

# iday_csv_templates
This repository contains the data template sample for initial iday set-up and instructions to generate the data for your Iday event.

# Getting started

## Prepare the environment
* The firts step is prepare your computer to work and verify csv files.
   * You can use the csv editor that you preffer, but it is necesary to avoid to add formating or extra information to these files
   * Due that we recomend to use VSCode to edit and check the format of csv files. [Download here](https://code.visualstudio.com/)
   * After download VSCode it will be very recomendable to add the extension **Rainbow CSV** which includes a csv validator.
   * After all opening a csv using VSCode will be seen like this:
   <br/><br/>
   ![alt text][rainbow]

## Download the files

[Download the files here](https://github.com/The-three-lords/iday_csv_templates/archive/refs/heads/main.zip)

After unzip this zip you can find 2 folders and one Readme.md.
* The **readme.md** is the file which contain the instructions.
* The **media** folder contains images for the intructions file
* The **csv-samples** is the folder which you are going to change and send to the set-up responsable of your iday event.
* From this point we only deal with the files inside **csv-samples** folder.

> Notice: If you are familiar with git repository, you can ask to the set-up responsable of your iday event for a branch in a private repository to add, check and upload the your iday event data

## Open csv-samples as a proyect in your VSCode

To open csv-samples, right-click on csv-samples folder and click on Open with --> Viscual code.
<br/><br/>
![alt text][open]

After that you are prepared to change and maniputale the sample file data with the information necessary for your iday event.
![alt text][vscode]


# Adding your iday event data

In this section we will check the folder files structure, the data structure, the meaning of every column of information and the way to validate it.

## Folder structure

In csv-samples folder you can find 4 files
* group.csv
* group_slots.csv
* user.csv
* user_slots.csv

### group.csv
This file contains the sample data of a configuration of seven hipotetical gruops of a event. All the data, **except the first line** have to be replaced for real data.
> Notice: Keep the correlative numbers to do it easier

#### Columns of the file
* ⚠️ **id:** This is the technical identificator of the group inside the application. Starting at **1000** all groups shoud have a correlative incremental number.
> 💬 Os parece bien?
* ⚠️ **innovation_day_id:** This column represents the event. The value for this column have to be **always 100**
> 💬 Creamos el 100?
* **name:** The name of the group. 
>Tip: Keep it simple
* **description**: The description of the group
* **fragments**: The number of fragments obtained by group. **Always 0**
* **responsable**: The mail of the responsable of this gruop. This mail have to conincide exactly with the user email of the USER_RESPONSABLE role who is responsable of this group.
* ⚠️**sala**: The url of the meeting room defined for the team. This column could be empty. As 1002 row sample data.
> 💬 Es cierto se puede dejar vacía sin implicaciones?
* ⚠️**is_completed**: Part of the status of the group. **Always 0**
> 💬 Esto se usa? Podemos ponerlo como default a 0?
* ⚠️**chosen_communication**: The name of choosen comunication application for the group. It could be empty
> 💬 Esto se usa? Podemos dejarlo vacío
* ⚠️**responsable2**: **Always admin@admin.com**
> 💬 Esto se usa?
### group_slots.csv
This file contains all empty groups which will be configured in your event. In the sample there are configured 10 groups which will be able to be configured during the event.
The column meaning are exactly the same than [group.csv](#groupcsv)

>Notice: With exceptions you don't need to change this file

>Notice: The slots groups always have the correlative identifier starting by **10000**

## user.csv
This file contains the sample data of a configuration of 3 hipotetical reponsables and 21 users. All the data, **except the first line** have to be replaced for real data. 
> Notice: Keep the correlative numbers to do it easier

#### Columns of the file
* ⚠️ **id:** This is the technical identificator of the user inside the application. 
   * Starting at **10000** all users shoud have a correlative incremental number.
   * Starting at **1000000** for responsables, all responsables shoud have a correlative incremental number.
> 💬 Os parece bien?
* **grupo_id**: This column is the connection between groups and users. Here you have to put the identificator of the group which user belongs.
   >⚠️ All responsable user have to be connected with 10000
* **email**: The email of the user
* **first_name**: The first name of the user
* **sur_name**: The sur name of the user
* **roles**: The posible values in this column are:
   * ROLE_ADMIN
   * ROLE_RESPONSABLE
   * ROLE_USER
* **password**: The password of the user
> 💬 Que hacemos con esto? Siempre el mismo o merece la pena generarlos?
* **first_time**: Always **0**
> 💬 Esto en que afecta?
* **image**: Always **defaultImg.png**,
> 💬 Default value?
* **fortaleza**: Always **a:0:{}**
> 💬 Default value?

<br/>

# Validating csv
If you are using VSCode and you have installed CSV Rainbow, you can execute a csv lint which can tell you if the format of the file is correct or have some mistakes.

![alt text][csvlint]

If you want to check the format of the csv file which **you have opened and focused in the screen**, you need to click in this green link and it will be lauched. It all is ok, the link will keep the green color if not it will change to red.

![alt text][badcsvlint]

>⚠️ Before any action in database we will execute this linter for all the files. If some file gives an error it will be returned to responsable to be ammended.
