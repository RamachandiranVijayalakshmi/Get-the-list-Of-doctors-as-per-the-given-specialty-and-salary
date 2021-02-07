## Get-the-list-Of-doctors-as-per-the-given-specialty-and-salary
## Sample code to check 
```sh
import mysql.connector

def get_connection():
    connection = mysql.connector.connect(host='localhost',
                                         database='python_db',
                                         user='pynative',
                                         password='pynative@#29')
    return connection

def close_connection(connection):
    if connection:
        connection.close()

def get_specialist_doctors_list(speciality, salary):
    try:
        connection = get_connection()
        cursor = connection.cursor()
        sql_select_query = """select * from Doctor where Speciality=%s and Salary > %s"""
        cursor.execute(sql_select_query, (speciality, salary))
        records = cursor.fetchall()
        print("Printing doctors whose specialty is", speciality, "and salary greater than", salary, "\n")
        for row in records:
            print("Doctor Id: ", row[0])
            print("Doctor Name:", row[1])
            print("Hospital Id:", row[2])
            print("Joining Date:", row[3])
            print("Specialty:", row[4])
            print("Salary:", row[5])
            print("Experience:", row[6], "\n")
        close_connection(connection)
    except (Exception, mysql.connector.Error) as error:
        print("Error while getting data", error)

print("Question 3: Get Doctors as per given Speciality\n")
get_specialist_doctors_list("Garnacologist", 30000)
```
## Example Output
Doctor Id: 103
Doctor Name: Susan
Hospital Id: 2
Hospital Name: Cleveland Clinic
Joining Date: 2016-05-19
Specialty: Garnacologist
Salary: 25000
Experience: None 

Doctor Id: 104
Doctor Name: Robert
Hospital Id: 2
Hospital Name: Cleveland Clinic
Joining Date: 2017-12-28
Specialty: Pediatric 
Salary: 28000
Experience: None
