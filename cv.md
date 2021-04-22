**Junior Developer Resume**

1. **Sergey Karpik**
2. My e-mail (serg.karpik@gmail.com)
3. Well, my aim is find work in wich my knowledge will be used and where i will be able to enrich it.
It's really important for me to continue learning something useful in future work.
I'm willing to learn, communicative and energetiс. I always took part in college activities and almost all of them were appreciated. 
I enjoy working in team, sometimes I had to be leader in different activities. I always try to do my best.
4. I was learning C++ and Java, worked in VisualStudio, QtCreator, IntelliJ IDEA and Android Studio
5. Avalible upon request (i didn't display my projects on GitHub, so i'll show code here)
```C++
#include "pch.h"
#include <iostream>

struct List {
	int key;
	List *next;
};

void Insert(List** Head, int &x) // Односвязный список

{
	// вставка в список одного элемента перед элементом,
	// большим или равным данному x
	List *p = new List;
	p->key = x;
	if (*Head == NULL) // исходный список пуст - вставка в начало
	{
		p->next = NULL;
		*Head = p;
		return;
	}
	List *t = *Head;
	if (t->key <= p->key) // исходный список не пуст -
	// вставка в начало
	{
		p->next = t;
		*Head = p;
		return;
	}
	List *t1 = t->next;
	while (t1 != NULL)
	{
		if (t->key > p->key && p->key >= t1->key)
		{ // вставка в середину
			t->next = p;
			p->next = t1;
			return;
		}
		t = t1;
		t1 = t1->next;
	}
	t->next = p; // добавляем в конец списка
	p->next = 0;
}

void Print(List * Head)
{
	List *p = Head;
	printf("Spisok:\n");
	while (p != NULL)
	{
		printf("%d \n",p->key);
		p = p->next;
	}
}

int Summ(List * Head)
{
	int summ= 0;
	List *p = Head;
	while (p != NULL)
	{
		summ += p->key;
		p = p->next;
	}
	return summ;
}

void Clear(List ** Head)
{
	// удаление (очистка) всего списка
	if (*Head == NULL) return;
	List *p = *Head;
	List *t;
	while (p != NULL)
	{
		t = p;
		p = p->next;
		delete t;
	}
	*Head = NULL;
	printf("List was deleted\n");
}

struct List2 //Двусвязный список
{
	int key;
	List2* prev;
	List2* next;
};

void Insert2_first(List2** Head, int &x) 
{
	List2 *p = new List2;
	p->key = x;
	List2* t = *Head;

	if (*Head != NULL)
	{
		p->next = *Head;
		t->prev = p;
		p->prev = NULL;
		*Head = p;
		return;
	}
	else
	{
		printf("Queue is empty");
		*Head = p;
	}
	return;
}

void Insert2_last(List2** Head, int &x) 
{
	List2 *p = new List2;
	p->key = x;


	if (*Head == NULL) // исходный список пуст - вставка в начало
	{
		p->next = NULL;
		p->prev = NULL;
		*Head = p;
		return;
	}

	List2 *t1 = *Head;

	while (t1 != NULL)
	{
		if (t1->next != NULL) {
			t1 = t1->next;
		}
		else
			break;

	}

	t1->next = p;
	p->next = NULL;
	p->prev = t1;

	

}

void Insert2_middle(List2** Head, int &x) 
{
	int cn = 0;
	List2 *p = new List2;
	p->key = x;
	List2 *t1 = *Head;

	if (*Head == NULL) // исходный список пуст - вставка в начало
	{
		p->next = NULL;
		p->prev = NULL;
		*Head = p;
		return;
	}

	if (t1->next == NULL) // исходный список 1 el - вставка в pos 2
	{
		p->next = NULL;
		p->prev = t1;
		t1->next = p;
		return;
	}

	while (t1 != NULL)
	{
		if (t1->next != NULL) {
			t1 = t1->next;
			cn++;
		}
		else {
			cn = cn / 2;
			break;
		}

	}

	t1 = *Head;

	for(int i=0; i < cn; i++)
	{	
			t1 = t1->next;
	}

	List2* tmp;
	tmp = t1->next;
	p->next = t1->next;
	p->prev = t1;
	t1->next = p;
	tmp->prev = p;
   

}

void Print2(List2 * Head)
{
	List2 *p = Head;

	printf("Spisok:\n");
	while (p != NULL)
	{
		if (p->next != NULL) {
			p = p->next;
		}
		else
			break;
	}

	while (p != NULL)
	{
		printf("%d \n", p->key);
		p = p->prev;

	}
}

int Proizv2(List2* Head)
{
	
		int proizv = 1;
		List2 *p = Head;
		while (p != NULL)
		{
			proizv *= p->key;
			p = p->next;
		}
		return proizv;
	
}

void Clear2(List2 ** Head)
{
	// удаление (очистка) всего списка
	if (*Head == NULL) return;
	List2 *p = *Head;
	List2 *t;
	while (p != NULL)
	{
		t = p;
		p = p->next;
		delete t;
	}
	*Head = NULL;
	printf("List2 was deleted\n");
}

int main()
{
	
     List* head = new List;
	 head->key = 1337;
	 head->next = NULL;
	 for (int i = 0; i < 10; i++)
	 {
     int buff;
	 buff = (int)i * 2 / 3;
	
		 Insert(&head, buff);
	 
	 }
	 Print(head);
	 printf("Summ = %d\n", Summ(head));
	 Clear(&head);
	 
	 
	// number 3

	 List2* head2 = new List2;
	 head2->key = 240;
	 head2->next = NULL;
	 head2->prev = NULL;

	 for (int i = 0; i < 4; i++)
	 {

		 Insert2_middle(&head2, i);
		 //Insert2_first(&head2, i);
		// Insert2_last(&head2, i);

	 }

	 Print2(head2);
	 printf("Proizv = %d\n", Proizv2(head2));
	 Clear2(&head2);
}
```
6. I was leading creating english dictionary with small group of active students in QtCreator using SQlite.
Also I created calculator with GUI as course project.
I'm working on learning Android Studio and have created some test applications (ex. Application to find out what kind of your temperament)
7. General secondary education,Now studing in Minsk Radioengineering College. Was learning English in "International House". 
8. Upper-intermediate, often use in everyday life to learn something new, to watch films, reaf sci-fi and listen to music.
9. Well, that was my old CV, but in task was mentioned that even imaginary is ok, so i just must pay your attention on it. Now Im interested in **Java/Kotlin** Android developent.
