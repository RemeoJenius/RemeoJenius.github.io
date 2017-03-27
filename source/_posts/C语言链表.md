---
title: C语言链表
date: 2017-03-24 18:06:43
tags:
---
## 链表
## 代码 linked-list.c
``` c
#include "node.h"
#include <stdio.h>
#include <stdlib.h>

// typedef struct _node{
// 	int value;
// 	struct _node *next;
// }Node;

typedef struct _list{ // 没有做尾指针
	Node *head;
	Node *tail;
} List;


void add(List *list, int number);
void add2(List *list, int number);

int main(int argc, char const *argv[])
{
	List list;
	list.head = list.tail = NULL;
	int number;
	do{
		scanf("%d",&number);
		if(number != -1){
			add2(&list,number);
		}
	}while(number != -1);
	for (Node *q = list.head;q;q=q->next){
		printf("%d",q->value);
	}
	return 0;
}

void add(List *list, int number){
	// add to linked-list
	Node *p = (Node*)malloc(sizeof(Node));
	p->value = number;
	p->next = NULL;
	// find last node
	Node *last = list->head;
	if(last){
		while(last->next){
			last = last->next;
		}
		last->next = p;
	}else{
		list->head = p;
	}


}

void add2(List *list, int number){  // 哎，早画图早解决了服了
	// add to linked-list
	Node *p = (Node*)malloc(sizeof(Node));
	p->value = number;
	p->next = NULL;
	// find last node
	if(list->tail){
		(list->tail)->next = p;
		list->tail = (list->tail)->next;

	}else{
		list->head = list->tail = p;

	}

}
```
