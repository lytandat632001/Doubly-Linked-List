#include<iostream>
using namespace std;
struct Time
{
	int Date;
	int Month;
	int Year;	
};
struct HangHoa
{
	string MaMay,TenMay,HangSX;
	float GiaTien;
	Time NgayBan;
		
};
typedef struct Node
{
	HangHoa Data;
	Node *Prev;
	Node *Next;
}Nodetype;
typedef Nodetype *Nodeptr;

Nodeptr CreateNode(HangHoa x)
{
	Nodeptr p;
	p=new Node;
	p->Data=x;
	p->Prev=NULL;
	p->Next=NULL;
	return p;
}
void InsertFirst(Nodeptr &Head,Nodeptr &Tail,Nodeptr p)
{

	if(Head==NULL)
	{
		Head=p;
		Tail=p;
	}
	else
	{
		p->Next=Head;
		Head->Prev=p;
		Head=p;
	}
}
void InsertLast(Nodeptr &Head,Nodeptr &Tail,Nodeptr &p)
{

	if(Head==NULL)
	{
		Head=p;
		Tail=p;
	}
	else
	{
		Tail->Next=p;
		p->Prev=Tail;
		Tail=p;
	}
}
void CreateList(Nodeptr &Head,Nodeptr &Tail)
{	
	HangHoa x;
	Nodeptr p;	
		fflush(stdin);
		getline(cin,x.MaMay)<<"  ";
		getline(cin,x.TenMay)<<"  ";
		getline(cin,x.HangSX)<<"  ";
		cout<<x.GiaTien<<"  ";
		cout<<x.NgayBan.Date<<"  ";
		cout<<x.NgayBan.Month<<"  ";
		cout<<x.NgayBan.Year<<"  ";
		p=CreateNode(x);
		InsertLast(Head,Tail,p);

}
void In(Nodeptr Head,Nodeptr Tail)
{	cout<<"Danh sach dong ho thong minh: "<<endl;
    while(Head!=NULL)
	{
		cout<<Head->Data.MaMay<<"  ";
		cout<<Head->Data.TenMay<<"  ";
		cout<<Head->Data.HangSX<<"  ";
		cout<<Head->Data.GiaTien<<"  ";
		cout<<Head->Data.NgayBan.Date<<"  ";
		cout<<Head->Data.NgayBan.Month<<"  ";
		cout<<Head->Data.NgayBan.Year<<"  ";
		Head=Head->Next;
		cout<<endl;
	}	
}

int main()
{	Nodeptr Head, Tail;
	Head=Tail=NULL;
/*
	HangHoa a={"AP01","Apple Wath  Series 3","Apple",7.2,10,5,2019};
	HangHoa  b={"FB01","Fitbit Versa","Fitbit",4.3,15,5,2018};
	HangHoa c={"GL01","Galaxy Watch 2018","Samsung",6.5,1,6,2018};
	CreateList(Head,Tail,a);
	CreateList(Head,Tail,b);
	CreateList(Head,Tail,c);*/
	CreateList(Head,Tail);
	In(Head,Tail);
/*
	cout<<"Danh sach dong ho thong minh nhap trong thang 5 nam 2018: ";
	for(int i=0;i<3;i++)
	{
	if(Head->Data.NgayBan.Month==5 && Head->Data.NgayBan.Year==2018)
	{
		cout<<Head->Data.MaMay<<"  ";
		cout<<Head->Data.TenMay<<"  ";
		cout<<Head->Data.HangSX<<"  ";
		cout<<Head->Data.GiaTien<<"  ";
		cout<<Head->Data.NgayBan.Date<<"  ";
		cout<<Head->Data.NgayBan.Month<<"  ";
		cout<<Head->Data.NgayBan.Year<<"  ";
		Head=Head->Next;
		cout<<endl;
	}
	else
	{
		Head=Head->Next;
	}
	}
*/
	return 0;
}
