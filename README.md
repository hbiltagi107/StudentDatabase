/***************************************************************
StudentDatabaseProgram.h
Huda Biltagi
5 / 2019
*************************************************************/

#include<iostream>
#include<string>
#include<iomanip>
using namespace std;

// Base student class
class Student  
{
private:

string fname;	// stores student first name
string lname;	// stores student last name
int	idnum;		// stores student ID Number

public:

// default student constructors 
Student()	
{
	
	fname = " ";
	lname = " ";
	idnum = 0;
		
}

// custom Student constructor
Student(string fn, string ln, int idn) 
{
	fname = fn;
	lname = ln;
	idnum = idn;
}

// Get/set first name 
string getfirstname()
{
	return fname;
}

void setfirstname(string f)
{
	fname = f;
}

// Get/set last name 
string getlastname()
{
	return lname;
}

void setlastname(string l)
{
	lname = l;
}

// Get/set ID Number 
int getIdNum()
{
	return idnum;
}

void setId(int id)
{
	idnum = id;
}


virtual void display()
{
	cout << "Below is the student database." << endl;
	
}
	
};

// Derived Elementary Student class
class ElementaryStu : public Student
{
private:

	int ElemGrade;   // stores elementary grade level (1,2,4,5..)

public:

// Default elementary student constructors 
ElementaryStu()	 
{

	ElemGrade = 0;
}
	
// Custom elementary student constructor
ElementaryStu(int e_g, string e_fn, string e_ln, int e_idn)
{
	ElemGrade = e_g;
	setfirstname(e_fn);
	setlastname(e_ln);
	setId(e_idn);
}

// Get/set grade 
int getGrade()
{
	return ElemGrade;
}

void setgrade(int eg)
{
	ElemGrade = eg;
}

// Prints elementary student information
 void display()
{
	cout << setw(16) << "Student's name :" << setw(4) << getfirstname() << "  " << getlastname() << endl;
	cout << setw(16) << "ID Number: " << setw(4) << getIdNum() << endl;
	cout << setw(16) << "Student's grade: "  << ElemGrade << endl << endl;
} 

};

class MiddleStu : public Student
{

private:

int MidGrade;	// stores middle school grade

public:

// Default middle school constructor
MiddleStu()	
{
	MidGrade = 0;
}

// custom middle school constructor
MiddleStu(int mg, string m_fn, string m_ln, int m_idn) 
{
	MidGrade = mg;
	setfirstname(m_fn);
	setlastname(m_ln);
	setId(m_idn);
}


// Get/set grade 
int getGrade()
{
	return MidGrade;
}

void setgrade(int mg)
{
	MidGrade = mg;
}
// Prints middle school student information
 void display()
{
	cout << setw(16) << "Student's name: " << setw(4) << getfirstname() << "  " << getlastname() << endl;
	cout << setw(16) << "ID Number: " << setw(4)  << getIdNum() << endl;
	cout << setw(16) << "Student's grade: "  << MidGrade << endl << endl;
}

};


/***************************************************************
StudentDatabaseProgram_Driver.cpp
Huda Biltagi
 5/2019
*************************************************************/

using namespace std;
int main()
{

	system("color b1");
	cout << "Hello!! Welcome to the Student Database Program for Stonegate School" << endl;
	cout << "---------------------------------------------------------" << endl << endl;
	cout << endl << endl;
	char choice, choice2, choice3;

	while (1)
	{

		cout << "\t\t====== STUDENT DATABASE MANAGEMENT SYSTEM ======";
		cout << "\n\n                                          ";
		cout << "\n\n";
		cout << "\n \t\t\t 1. Add  Records";
		cout << "\n \t\t\t 2. List Records";
		cout << "\n \t\t\t 3. Exit Program";
		cout << "\n\n";
		cout << "\t\t\t Select Your Choice :=> ";
		cin >> choice;


		switch (choice)
		{
		case '1':
			choice2 = 'Y';
			while (choice2 == 'Y' || choice2 == 'y')
			{
				string first_name, last_name;
				int grade, IDnum;
				ElementaryStu es1;
				MiddleStu ms1;
				cout << "Enter the students First Name: ";
				cin >> first_name;
				cout << "Enter the students Last Name : ";
				cin >> last_name;
				cout << "Enter the students ID number : ";
				cin >> IDnum;
				cout << "Enter the Students Grade: ";
				cin >> grade;
				if (grade <= 5){
					es1.setfirstname(first_name);
					es1.setlastname(last_name);
					es1.setId(IDnum);
					es1.setgrade(grade);
					cout << "Your Elementary Student's information has been added as follows: " << endl;
					es1.display();
				}		
				else{
					ms1.setfirstname(first_name);
					ms1.setlastname(last_name);
					ms1.setId(IDnum);
					ms1.setgrade(grade);
					cout << "Your Middle School tudent's information has been added as follows: " << endl;
					ms1.display();
				}
					
				

			cout << "\n Add Another Record (Y/N) ";
			cin >> choice2;
			}
			break;

		case '2':
			cout << "=== View the Records in the Database ===";
			cout << "\n";
			choice3 = 'Y';
			while (choice3 == 'Y' || choice3 == 'y')
			{

				// local variables for arrays
				const int NUM_CLASSROOM_STUDENTS = 10;
				int index = 0; // index counter


				// Array of Elemntary Student objects

				ElementaryStu Mrs_DuggansClassroom[NUM_CLASSROOM_STUDENTS] = { ElementaryStu(2,"Sarah", "Willson", 2000),
																				ElementaryStu(2,"Jessica", "Offers", 2001),
																				ElementaryStu(2,"Amia", "Vest",2002),
																				ElementaryStu(2,"Evalina", "Tuttle",2003),
																				ElementaryStu(2,"John", "Smith",2004),
																				ElementaryStu(2,"Evan", "Jakoob",2005),
																				ElementaryStu(2,"Sevet", "Johns",2006),
																				ElementaryStu(2,"Willow", "Andrew",2007),
																				ElementaryStu(2,"Watson", "Levins",2008),
																				ElementaryStu(2,"Jackson", "Tu",2009) };

				// For loop to display the classroom roster
				cout << "---------------------------------------------------------" << endl << endl;
				cout << "Mrs. Duggans 2nd grade elementary classroom roster:" << endl << endl;
				cout << "---------------------------------------------------------" << endl << endl;

				for (index; index < NUM_CLASSROOM_STUDENTS; index++)
				{
					(Mrs_DuggansClassroom[index]).display();
				}



				// Array of Middle Student objects
				MiddleStu Mr_TraversoClassroom[NUM_CLASSROOM_STUDENTS] = { MiddleStu(7,"Witson", "Levers",7000),
																			MiddleStu(7,"Hannah", "Jenkins",7001),
																			MiddleStu(7,"Juan", "Homles",7002),
																			MiddleStu(7,"Emily", "Debrough",7003),
																			MiddleStu(7,"Alice", "DeSilva",7004),
																			MiddleStu(7, "Aviv", "Jetter", 7005),
																			MiddleStu(7, "Philip", "Finkel", 7006),
																			MiddleStu(7, "Greg", "Watson", 7007),
																			MiddleStu(7, "Kim", "Hughes", 7008),
																			MiddleStu(7, "Jose", "Sander", 7009) };


				// For loop to display the classroom roster
				cout << "---------------------------------------------------------" << endl << endl;
				cout << "Mr. Traverso's 7th Grade Middle School classroom roster:" << endl << endl;
				cout << "---------------------------------------------------------" << endl << endl;

				for (index; index < NUM_CLASSROOM_STUDENTS; index++)
				{
					(Mr_TraversoClassroom[index]).display();
				}

				cout << "\n\n";
				cout << "\n View Another Class (Y/N) ";
				cin >> choice3;
				
			}
			
			break;

		case '5':
			cout << "\n\n";
			cout << "\t\t     THANK YOU FOR USING THIS SOFTWARE";
			cout << "\n\n";
			exit(0);
		}
			
			
	}
return 0;
}
