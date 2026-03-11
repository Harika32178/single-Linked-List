# single-Linked-List
insertion and deletion operations
#include <bits/stdc++.h>
using namespace std;
struct Node {
    int data;
    Node* next;

    Node(int val) {
        data = val;
        next = NULL;
    }
};
    // insertion operations

    // insertion at beggining
    
void insertAtBeginning(Node*& head, int val) {
    Node* newNode = new Node(val);
    newNode->next = head;
    head = newNode;
}
    // insertion at the end

void insertAtEnd(Node*& head, int val) {
    Node* newNode = new Node(val);

    if(head == NULL) {
        head = newNode;
        return;
    }

    Node* temp = head;

    while(temp->next != NULL) {
        temp = temp->next;
    }

    temp->next = newNode;
}
    // insertion at the val at position
    
 void insertAtPosition(Node*& head, int pos, int val) {

    Node* newNode = new Node(val);

    if(pos == 1) {
        newNode->next = head;
        head = newNode;
        return;
    }

    Node* p1 = head;

    for(int i = 1; i < pos-1 && p1 != NULL; i++) {
        p1 = p1->next;
    }

    if(p1 == NULL) return;

    Node* p2 = p1->next;

    p1->next = newNode;
    newNode->next = p2;
}

    // deletion operations
    
    // delete first node
    
void deleteFirst(Node*& head) {
    if(head == NULL) return;

    Node* temp = head;
    head = head->next;
    delete temp;
}


// delete last node


void deleteLast(Node*& head) {

    if(head == NULL) return;

    if(head->next == NULL) {
        delete head;
        head = NULL;
        return;
    }

    Node* temp = head;

    while(temp->next->next != NULL) {
        temp = temp->next;
    }

    delete temp->next;
    temp->next = NULL;
}


// delete node at position
void deleteAtPosition(Node*& head, int pos) {

    if(head == NULL) return;

    if(pos == 1) {
        deleteFirst(head);
        return;
    }

    Node* temp = head;

    for(int i = 1; i < pos-1 && temp != NULL; i++) {
        temp = temp->next;
    }

    if(temp == NULL || temp->next == NULL) return;

    Node* nodeToDelete = temp->next;
    temp->next = temp->next->next;

    delete nodeToDelete;
}
    void printList(Node* head){
    while(head){
        cout << head->data << " -> ";
        head = head->next;
    }
    cout << "NULL";
}
    
