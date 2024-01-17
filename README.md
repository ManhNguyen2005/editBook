#include <bits/stdc++.h>
#include <iostream>
#include <iomanip>
#include <bits/stdc++.h>
#include <io.h>
#include <fcntl.h>

using namespace std;

int editBook()
{
    ifstream xvtk("book.txt"); 
    string A[100][8], x;

    int run = 0; 
    
    while (getline(xvtk, x)) 
    {
        string isbn = "", title = "", subject = "",
               author = "", publisher = "", date = "", pages = "", copies = "";

        int kt = 0;
        for (size_t i = 0; i < x.size(); ++i)
        {
            if (x[i] == ' ')
            {
                if (kt == 0)
                {
                    kt = 1;
                    continue;
                }
                if (kt == 1)
                {
                    kt = 2;
                    continue;
                }
                if (kt == 2)
                {
                    kt = 3;
                    continue;
                }
                if (kt == 3)
                {
                    kt = 4;
                    continue;
                }
                if (kt == 4)
                {
                    kt = 5;
                    continue;
                }
                if (kt == 5)
                {
                    kt = 6;
                    continue;
                }
                if (kt == 6)
                {
                    kt = 7;
                    continue;
                }
            }

            if (kt == 0)
            {
                isbn += x[i];
            }
            if (kt == 1)
            {
                title += x[i];
            }
            if (kt == 2)
            {
                subject += x[i];
            }
            if (kt == 3)
            {
                author += x[i];
            }
            if (kt == 4)
            {
                publisher += x[i];
            }
            if (kt == 5)
            {
                date += x[i];
            }
            if (kt == 6)
            {
                pages += x[i];
            }
            if (kt == 7)
            {
                copies += x[i];
            }
        }

        A[run][0] = isbn;
        A[run][1] = title;
        A[run][2] = subject;
        A[run][3] = author;
        A[run][4] = publisher;
        A[run][5] = date;
        A[run][6] = pages;
        A[run][7] = copies;
        run++;
    }
    cout<<"\t\t\t\t\t\t\t\t\t\tMENU SACH\n";
    cout<<"\t\t\t\t\t\t\t\t\t   __________________"<<endl;
	cout<<setw(8)<<left<<"Id sach"<<"|"<<setw(45)<<left<<"Ten sach"<<"|"<<setw(25)<<left<<"Chu de"<<"|"<<setw(25)<<left<<"Tac gia"<<"|"<<setw(25)<<left<<"Nha xuat ban"<<"|"
	<<setw(6)<<left<<"Nam xb"<<"|"<<setw(5)<<left<<"Trang"<<"|"<<setw(7)<<left<<"Ban sao"<<"|"<<endl;
	cout<<"__________________________________________________________________________________________________________________________________________________________"<<endl;
	for (int _ = 0; _ < sizeof(A) / sizeof(A[0]); _++)
    {
        if (A[_][0] == "")
        {
            continue;
        }
        cout <<setw(8)<<left<<A[_][0]<< "|" <<setw(45)<<left<< A[_][1] << "|" <<setw(25)<<left<<A[_][2] << "|" <<setw(25)<<left<<A[_][3] << "|" <<setw(25)<<left<<A[_][4] << "|" 
		<<setw(6)<<left<<A[_][5] << "|" <<setw(5)<<left<<A[_][6] << "|" <<setw(7)<<left<<A[_][7]<<"|"<< "\n";
    }
    xvtk.close();
	fstream ofs;
	ofs.open("book.txt");
	while (true) {
        int index = -1;
        string name;

        cout << "Nhap ten sach: ";
        cin >> name;

        // Searching for the book
        for (size_t i = 0; i < run; i++) {
            if (A[i][0] == name || A[i][1] == name) {
                index = i;
                break; // Exit the loop once the book is found
            }
        }

        if (index != -1) {
            // Display book information
        	cout << setw(8) << left << A[index][0] << "|" << setw(45) << left << A[index][1] << "|" << setw(25) << left << A[index][2] << "|"
                << setw(25) << left << A[index][3] << "|" << setw(25) << left << A[index][4] << "|" << setw(6) << left << A[index][5] << "|"
                << setw(5) << left << A[index][6] << "|" << setw(7) << left << A[index][7] << "|" << "\n";
            cout<<"----------Menu Chinh sua----------"<<endl;
            cout<<"1.Id sach.\n2.Ten sach.\n3.Chu de.\n4.Tac gia.\n5.Nha xuat ban.\n6.Nam xuat ban.\n7.So trang.\n8.So ban sao.\n9.Thoat\n";
            int choice;
            cout<<"Nhap lua chon: ";cin>>choice;
            switch (choice){
            	case 1:{
            		string id;
            		cout<<"Nhap id moi: ";cin>>id;
            		A[index][0] = id;
            		ofs<<A[index][0];
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\n";
					cout<<"Ban co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 2:{
            		string name;
            		cout<<"Nhap ten moi: ";cin>>name;
            		A[index][1] = name;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 3:{
            		string subject;
            		cout<<"Nhap chu de moi: ";cin>>subject;
            		A[index][2] = subject;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					}
            		else break;
            		//break;
            	}
            	case 4:{
            		string author;
            		cout<<"Nhap ten tac gia moi: ";cin>>author;
            		A[index][3] = author;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 5:{
            		string publisher;
            		cout<<"Nhap nxb moi: ";cin>>publisher;
            		A[index][4] = publisher;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 6:{
            		string date;
            		cout<<"Nhap nam xb moi: ";cin>>date;
            		A[index][5] = date;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 7:{
            		string pages;
            		cout<<"Nhap so trang moi: ";cin>>pages;
            		A[index][6] = pages;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 8:{
            		string copies;
            		cout<<"Nhap so ban sao moi: ";
            		A[index][7] = copies;cin>>copies;
            		cout<<A[index][0]<<"|"<<A[index][1]<<"|"<<A[index][2]<<"|"<<A[index][3]<<"|"<<A[index][4]<<"|"<<A[index][5]<<"|"<<A[index][6]<<"|"<<A[index][7]<<endl;
            		cout<<"Sua thanh cong.\nBan co muon chinh sua tiep khong(Y/N): ";
            		string lc;
            		cin>>lc;
            		if (lc == "Y"){
            			system("cls");
            			continue;
					} 
            		else break;
            		//break;
            	}
            	case 9:{
					break;
				}
            	default:
            		break;
			}
			return 0;
        } else {
            cout << "Khong tim thay sach.\n";
            string yc;

            cout << "Ban co muon tim sach khac khong (Y/N): ";
            cin >> yc;

            if (yc != "Y")
                return 0; // Return 0 to indicate successful program termination
        }
	}
	ofs.close();
	//return 0;
}
int main()
{
	editBook();
	return 0;
}
