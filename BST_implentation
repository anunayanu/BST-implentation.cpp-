#include<iostream>
#include<queue>
using namespace std;

struct BstNode
{

    int data;
    BstNode* left;
    BstNode* right;

  /**

    BstNode(int data)
    {
        this->data=data;
        left=right=NULL;
    }

       */

};


BstNode* getNewNode(int data)
{

    BstNode* node = new BstNode();
    node->data=data;
    node->left = node->right =NULL;
    return node;

}

BstNode* insertNode(BstNode* root, int data)
{

    if(root==NULL)
        root=getNewNode(data);
    else if (data <= root->data)
        root->left=insertNode(root->left,data);
    else
        root->right=insertNode(root->right,data);

    return root;

}

bool search(BstNode* root, int data)
{

    if(root==NULL)
        return false;
    else if(root->data==data)
        return true;
    else if(data <= root->data)
        return search(root->left, data);
    else
        return search(root->right, data);

}

int minElement(BstNode* root)
{

    /**
    * ***   recursive method

      if(root == NULL)
          return 0;
      else if(root->left==NULL)
          return root->data;
      else
          minElement(root->left);         **/

    if(root == NULL)
        return 0;
    while(root->left!=NULL)
        root=root->left;
    return root->data;
}

int maxElement(BstNode* root)
{

    /**
    * ***   recursive method

    if(root == NULL)
        return 0;
    else if(root->right==NULL)
        return root->data;
    else
        minElement(root->right);

         **/

    if(root == NULL)
        return 0;
    while(root->right!=NULL)
        root=root->right;
    return root->data;

}

int height(BstNode* root)
{
    int leftHeight=0, rightHeight=0;

    if(root==NULL)
        return -1;

    leftHeight = height(root->left);
    rightHeight = height(root->right);

    return max(leftHeight, rightHeight)+1;

}

void levelOrderTraversal(BstNode* root)
{
    /**   time complexity is O(n)   */

    if(root==NULL)
        return;
    queue<BstNode*> q;
    q.push(root);

    while(root!=NULL)
    {
        BstNode* current = q.front();
        cout<<current->data<<" ";

        if(current->left!=NULL)
            q.push(current->left);
        if(current->right!=NULL)
            q.push(current->right);
        q.pop();

    }
}

void preOrder(BstNode* root)
{
    if(root==NULL)
        return ;
    cout<<root->data<<" ";
    preOrder(root->left);
    preOrder(root->right);
}

void inOrder(BstNode* root)
{
    if(root==NULL)
        return ;

    inOrder(root->left);
    cout<<root->data<<" ";
    inOrder(root->right);
}

void postOrder(BstNode* root)
{
    if(root==NULL)
        return ;

    postOrder(root->left);
    postOrder(root->right);
    cout<<root->data<<" ";
}

int isBstUtil(BstNode* root, int min, int max)
{
    if(root==NULL)
        return 1;
    if(root->data<min || root->data>max)
        return 0;
    return isBstUtil(root->left, min, root->data-1) && isBstUtil(root->right, root->data+1, max);
}

int isBst(BstNode* root)
{
    return isBstUtil(root, INT_MIN, INT_MAX);
}

int isBstUsingInorder( BstNode* root)
{
    static BstNode *prev = NULL;

    // traverse the tree in inorder fashion and keep track of prev node
    if (root)
    {
        if (!isBstUsingInorder(root->left))
          return 0;

        // Allows only distinct valued nodes
        if (prev != NULL && root->data <= prev->data)
          return 0;

        prev = root;

        return isBstUsingInorder(root->right);
    }

    return 1;
}

BstNode* FindMinNode(BstNode* root)
{
	while(root->left != NULL) root = root->left;
	return root;
}

BstNode* deleteNode(BstNode* root, int data)
{
    if(root==NULL)
        return root;
    else if(data < root->data) root->left = deleteNode(root->left, data);
    else if (data > root->data) root->right = deleteNode(root->right, data);
    else {

        // case 1: No child
        if(root->left==NULL && root->right == NULL){
            delete(root);
            root=NULL;

        }// case 2 : one child
        else if(root->left==NULL)
        {
            BstNode* temp=root;
            root=root->right;
            delete temp;
        }else if(root->right==NULL)
        {
            BstNode* temp=root;
            root=root->left;
            delete temp;
        }
        //case 3: two child
        else{

            //BstNode* node = minElement(root->right);
            int minValue = minElement(root->right);
            root->data=minValue;
            root->right=deleteNode(root->right, minValue);

        }
    }

    return root;
}

BstNode* findNode(BstNode* root, int data)
{
    if(root==NULL)
        return root;

    else if(root->data == data)
            return root;

    else if(data < root->data) return findNode(root->left, data);

    else return findNode(root->right, data);
}

BstNode* inOrderSuccessorOfNode(BstNode* root, int data)
{
    BstNode* current = findNode(root, data);

    if(current == NULL)
        return NULL;

    //Case 1: Node has right subtree

    if(current->right!=NULL)
        return FindMinNode(current->right);
    else {   //Case 2: No right subtree  - O(h)
		 BstNode* successor = NULL;
		 BstNode* ancestor = root;
		while(ancestor != current) {
			if(current->data < ancestor->data) {
				successor = ancestor; // so far this is the deepest node for which current node is in left
				ancestor = ancestor->left;
			}
			else
				ancestor = ancestor->right;
		}
		return successor;
	}

}



int main()
{

    BstNode* root=NULL, *temp;
  /**  root=insertNode(root,20);
    root=insertNode(root,15);
    root=insertNode(root,12);
    root=insertNode(root,5);
    root=insertNode(root,1);
    root=insertNode(root,-1);

    **/

    int keys[] = { 15, 10, 20, 8, 12, 16, 25 };

	//for (int key : keys)
	for(int i=0;i<sizeof(keys)/sizeof(keys[0]);i++)
		root = insertNode(root, keys[i]);


     int s, delvalue, findSuccessorNodeOf;
     cout<<"Enter value to search "<<endl;
     cin>>s;

     if(search(root, s))
        cout<<"Found"<<endl;
    else cout<<"Not Found"<<endl;

   //  cout<<"Enter value to delete "<<endl;
   //  cin>>delvalue;

   //  deleteNode(root, delvalue);

   cout<<"Enter value to find inorder successor "<<endl;
   cin>>findSuccessorNodeOf;

   temp = inOrderSuccessorOfNode(root, findSuccessorNodeOf);
   if(temp==NULL)
    cout<<"Sorry Element is not present, can't find inorder successor !! "<<endl;
   else
      cout<<"In order successor of "<<findSuccessorNodeOf<<" is "<<(temp->data)<<endl;


    cout<<"Min Element : "<<minElement(root)<<endl;
    cout<<"Max Element : "<<maxElement(root)<<endl;

    cout<<"Height of tree : "<<height(root)<<endl;
    // levelOrderTraversal(root);
    cout<<endl;
    cout<<"Preorder traversal of tree "<<endl;
    preOrder(root);
    cout<<endl;
    cout<<"Inorder traversal of tree "<<endl;
    inOrder(root);
    cout<<endl;
    cout<<"Postorder traversal of tree "<<endl;
    postOrder(root);
    cout<<endl;

    int bst=isBstUsingInorder(root);

   // cout<<bst<<endl;

    if(bst)
        cout<<"BST"<<endl;
    else cout<<"Not BST"<<endl;

    return 0;
}
