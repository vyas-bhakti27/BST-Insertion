#include <stdio.h>  // Binary Search tree insertion
#include <stdlib.h>
 
struct node {
    int key;
    struct node *left, *right;
};
 

struct node* newNode(int item)
{
    struct node* temp = (struct node*)malloc(sizeof(struct node));
    temp->key = item;
    temp->left = temp->right = NULL;
    return temp;
}
 

void inorder(struct node* root)
{
    if (root != NULL) {
        inorder(root->left);
        printf("%d \n", root->key);
        inorder(root->right);
    }
}
 

struct node* insert(struct node* node, int key)
{
    
    if (node == NULL)
        return newNode(key);
 
    
    if (key < node->key)
        node->left = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
 
    
    return node;
}
 

int main()
{
    
    struct node* root = NULL;
    root = insert(root, 50);
    insert(root, 25);
    insert(root, 22);
    insert(root, 40);
    insert(root, 30);
    insert(root, 75);
    insert(root, 60);
    insert(root, 80);
    insert(root, 90);
 
   
    inorder(root);
 
    return 0;
}
