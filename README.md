# code
sqlite> CREATE TABLE ACTOR(
   ...> ACT_ID NUMBER(3),
   ...> ACT_NAME VARCHAR(20),
   ...> PRIMARY KEY(ACT_ID));
sqlite> CREATE TABLE DIRECTOR(
   ...> DIR_ID NUMBER(3),
   ...> DIR_NAME VARCHAR(20),
   ...> PRIMARY KEY(DIR_ID));
sqlite> CREATE TABLE ACTRESS(
   ...> ACTRSS_ID NUMBER(3),
   ...> ACTRSS_NAME VARCHAR(20),
   ...> PRIMARY KEY(ACTRSS_ID));
sqlite> CREATE TABLE MOVIE(
   ...> MOV_ID NUMBER(3),
   ...> MOV_NAME VARCHAR(20),
   ...> MOV_YEAR NUMBER(3),
   ...> ACT_ID NUMBER(3),
   ...> DIR_ID NUMBER(3),
   ...> ACTRSS_ID NUMBER(3),
   ...> PRIMARY KEY(MOV_ID),
   ...> FOREIGN KEY(ACT_ID) REFERENCES ACTOR(ACT_ID),
   ...> FOREIGN KEY(DIR_ID) REFERENCES DIRECTOR(DIR_ID),
   ...> FOREIGN KEY(ACTRSS_ID) REFERENCES ACTRESS(ACTRSS_ID));
sqlite> INSERT INTO ACTOR VALUES(12,'PRABHAS');
sqlite> INSERT INTO ACTOR VALUES(14,'RANVEER SINGH');
sqlite> INSERT INTO ACTOR VALUES(16,'RAJINIKANTH');
sqlite> INSERT INTO DIRECTOR VALUES(120,'S.S.Rajamouli');
sqlite> INSERT INTO DIRECTOR VALUES(140,'Sanjay_Leela_Bhansali');
sqlite> INSERT INTO DIRECTOR VALUES(160,'Shankar');
sqlite> INSERT INTO ACTRESS VALUES(1200,'ANUSHKA SHETTY');
sqlite> INSERT INTO ACTRESS VALUES(1400,'DEEPIKA PADUKONE');
sqlite> INSERT INTO ACTRESS VALUES(1600,'AISHWARYA RAI');
sqlite> INSERT INTO MOVIE VALUES(123,'BAAHUBALI',2015,12,120,1200);
sqlite> INSERT INTO MOVIE VALUES(456,'BAJIRAO MASTHANI',2016,14,140,1400);


import sqlite3

try:
    sqliteConnection = sqlite3.connect('sql.db')
    cursor = sqliteConnection.cursor()
 
 
    print("Successfully Connected to SQLite")
    cur = sqliteConnection.cursor()

 
    for row in cur.execute('SELECT * FROM MOVIE;'):
        print(row)
       

    
    cursor.close()

except sqlite3.Error as error:
    print("Error while executing sqlite script", error)
finally:
    if sqliteConnection:
        sqliteConnection.close()
        print("sqlite connection is closed")
sqlite> INSERT INTO MOVIE VALUES(789,'ROBOT',2010,16,160,1600);
sqlite> SELECT * FROM MOVIE
   ...> ;
