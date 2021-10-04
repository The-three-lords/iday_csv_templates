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

# iday_csv_templates

This repository contains the data template sample for initial iday set-up and instructions to generate the data for your Iday event.

# Getting started

## Prepare the environment

- The firts step is prepare your computer to work and verify csv files.
  - You can use the csv editor that you preffer, but it is necesary to avoid to add formating or extra information to these files
  - Due that we recomend to use VSCode to edit and check the format of csv files. [Download here](https://code.visualstudio.com/)
  - After download VSCode it will be very recomendable to add the extension **Rainbow CSV** which includes a csv validator.
  - After all opening a csv using VSCode will be seen like this:
    <br/><br/>
    ![alt text][rainbow]

## Download the files

[Download the files here](https://github.com/The-three-lords/iday_csv_templates/archive/refs/heads/main.zip)

After unzip this zip you can find 2 folders and one Readme.md.

- The **readme.md** is the file which contain the instructions.
- The **media** folder contains images for the intructions file
- The **csv-samples** is the folder which you are going to change and send to the set-up responsable of your iday event.
- From this point we only deal with the files inside **csv-samples** folder.

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

- group.csv
- group_slots.csv
- user.csv
- user_slots.csv

> ⚠️ Only it is necessary to change group.csv, user.csv and user_slots.csv

### group.csv

This file contains the sample data of a configuration of seven hipotetical gruops of a event. All the data, **except the first line** have to be replaced for real data.

> 🛑 For every new group which you create in this file, you will need to add a new row in user_slots.csv to haver an extra user_slot for this group. If not, during the event, you won't have slots for changes in this group. During the event will be imposible to add or delete users, thus it is very important to have empty slots for that. To create this new row, add a new row to user_slot.csv following the intructions of user.csv

> Notice: Keep the correlative numbers to do it easier

#### Columns of the file

For every new group copy and paste a row and change the columns, id, name, description, responsable and sala, as follows

⚠️Keep the values of innovation_day_id, fragments and is_completed

- **id:** This is the technical identificator of the group inside the application. Starting at **1000** all groups shoud have a correlative incremental number.

- **name:** The name of the group.

- **description**: The description of the group

- **responsable**: The mail of the responsable of this gruop. This mail have to conincide exactly with the user email of the USER_RESPONSABLE role who is responsable of this group.
- **sala**: The url of the meeting room defined for the team. This column could be empty. As 1002 row sample data.

- ⚠️**innovation_day_id:** This column represents the event. The value for this column have to be **Always 100** (⚠️do not change this value)

- ⚠️**fragments**: The number of fragments obtained by group. **Always 0** (⚠️do not change this value)

- ⚠️**is_completed**: Part of the status of the group. **Always 0** (⚠️do not change this value)

### group_slots.csv

This file contains all empty groups which will be configured in your event. In the sample there are configured 10 groups which will be able to be configured during the event.
The column meaning are exactly the same than [group.csv](#groupcsv)

> Notice: 🛑 With exceptions you don't need to change this file

> Notice: The slots groups always have the correlative identifier starting by **10000**

## user.csv

This file contains the sample data of a configuration of 3 hipotetical reponsables and 21 users. All the data, **except the first line** have to be replaced for real data.

> Notice: Keep the correlative numbers to do it easier

#### Columns of the file

- **id:** This is the technical identificator of the user inside the application.

  - Starting at **10000** all users shoud have a correlative incremental number.
  - Starting at **1000000** for responsables, all responsables shoud have a correlative incremental number.

- **grupo_id**: This column is the connection between groups and users. Here you have to put the identificator of the group which user belongs.
  > 🛑 All responsable user have to be connected with group 10000
- **email**: The email of the user
- **first_name**: The first name of the user
- **sur_name**: The sur name of the user
- **⚠️roles**: The posible values in this column are:
  - ROLE_ADMIN
  - ROLE_RESPONSABLE
  - ROLE_USER
    > ⚠️ If you create a ROLE_USER user, copy a ROLE_USER row, If yout create a ROLE_RESPONSABLE user, copy a ROLE_RESPONSABLE row. Thus keep the role in this row.
- **⚠️password**: The password of the user
  > ⚠️ If you create a ROLE_USER user, copy a ROLE_USER row, If yout create a ROLE_RESPONSABLE user, copy a ROLE_RESPONSABLE row. Thus keep the password of this row.
- **⚠️first_time**: Always **0** (⚠️do not change this value)

- **⚠️image**: Always **defaultImg.png** (⚠️do not change this value)

- **⚠️fortaleza**: Always **a:0:{}** (⚠️do not change this value)

## user_slots.csv

This file contains

- 2 slots for responsable user
- 60 user slots for slot groups (6 for slot group)
- 7 user slots for real groups.

If you create a new real group in group.csv, you will need to add a user_slot in this file to be able to add a new member in this group during the event.

<br/>

# Validating csv

If you are using VSCode and you have installed CSV Rainbow, you can execute a csv lint which can tell you if the format of the file is correct or have some mistakes.

![alt text][csvlint]

If you want to check the format of the csv file which **you have opened and focused in the screen**, you need to click in this green link and it will be lauched. It all is ok, the link will keep the green color if not it will change to red.

![alt text][badcsvlint]

> ⚠️ Before any action in database we will execute this linter for all the files. If some file gives an error it will be returned to responsable to be ammended.
