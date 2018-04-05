#This is a Tree object which allows navigating upwards, downwards and sideways if necessary.
#Not all of the functionalities in this tree have been used,
#but they have been left for further coding.
#A Depth First Search functionality has been added to this tree with dfs_search() method.
#This algorithm uses a list data structure as a stack and searches towards the descendants first,
#before going to the siblings.
#This is a first in last out recursive search.


#Creating a dictionary to add the instances of Tree. Good for reaching the root from any given point easily.
#And also for keeping the name of the object with it's instance.
tree_dict = {}
class Tree(object): 
   
    #References to both parent and child.
    def __init__(self, data, parent=None, children=None):
        self.children = children or []
        self.parent = parent
        self.data = data
        tree_dict[self] = data
        for child in self.children:
            child.parent = self
            
    #Adding new instances of Tree with reference to its parent. Only one parent.    
    def add_child(self, data):
        new_child = Tree(data, parent=self)
        self.children.append(new_child)
        return new_child
    
    #To check whether an instance is the root. Boolean
    def is_root(self):
        return self.parent is None
    
    #Finds the root as a Tree object.
    #If it cannot find it from the given point, looks for its parent.
    def get_root(self):
        for key, value in tree_dict.items():
            if self.parent is None:
                return self
            else:    
                return self.find_parent().get_root()
            
    #To check whether an instance is a leaf. Boolean            
    def is_leaf(self):
        return not self.children
    
    #Returns an object data in a pretty format with its children. Can be changed easily.
    def __str__(self):
        if self.is_leaf():
            return str(self.data)
        return '{data} [{children}]'.format(data=self.data, children=', '.join(map(str, self.children)))

    #Gets the children of the object as a list of tree objects
    def find_children(self):
        return self.children
    
    #Gets the parent of the node as Tree object.
    #If the object is the root, returns None
    def find_parent(self):
        if self.parent:
            return self.parent
        else:
            return None
        
    #Finds the siblings of the node as Tree objects. Excludes itself.    
    def find_sibling(self):
        if not self.is_root():      
            parent = self.parent
            sibling = parent.find_children()
            sibling.remove(self)
            return sibling
        else :
            return None
        
    #This is the Depth First Search Algorithm mentioned above.
    #Uses user input as a search term.
    def dfs_search(self):
        sought = input() 
        
        #Keep track of already visited nodes
        visited = set()
        
        #Move to the root of the tree first
        root = self.get_root()
        
        #This list used as a stack with pop() and extend() methods will 
        #provide first in last out algorithm.
        stack = [root]   
        
        #Recursive loop begins with the root node
        while stack:
            
            #Since pop() method returns the poped article, it can be the variable.
            node = stack.pop()
            if node in visited:
                pass
            else:
                
                #Check if it is what we are looking for.
                if node.data == sought:
                    print(node.data, "Found")
                    
                    #This is only to check if the search is moving through the tree
                    #as we want it. It can be commented out later.
                    for item in visited:
                        print(item.data)
                else: 
                    
                    #To establish the recursive algorithm
                    stack.extend(node.find_children())
                    
                    #To make sure we do not search the same node again.
                    visited.add(node)
                    
        #If the sought article is not in the tree            
        if stack == []:
            return False
          
              
#This is a tree to test the code
#This tree represent a small part of the legal system
#A relatively good example, since there is hierarchy.
#But not so good, because these can have more than one parent in reality. 
Law = Tree("Law")
Private_Law =Law.add_child("Private_Law")
Public_Law = Law.add_child("Public_Law")
Criminal_Law = Public_Law.add_child("Criminal_Law")
Constitutional_Law = Public_Law.add_child("Constitutional_Law")
Civil_Law = Private_Law.add_child("Civil_Law")
Family_Law = Civil_Law.add_child("Family_Law")
Contract_Law = Civil_Law.add_child("Contract_Law")
Administrative_Law = Public_Law.add_child("Administrative_Law")
Property_Law = Civil_Law.add_child("Property_Law")
Criminal_Procedure_Law = Criminal_Law.add_child("Criminal_Procedure_Law")
Civil_Procedure_Law = Civil_Law.add_child("Civil_Procedure_Law")
Private_International_Law = Private_Law.add_child("Private_International_Law")
Public_International_Law = Public_Law.add_child("Public_International_Law")
Tax_Law = Public_Law.add_child("Tax_Law")
Intellectual_Property_Law = Civil_Law.add_child("Intellectual_Property_Law")
Inheritance_Law = Civil_Law.add_child("Inheritance_Law")
Sales_Contract = Contract_Law.add_child("Sales_Contract")
Renting = Contract_Law.add_child("Renting")
Borrowing = Contract_Law.add_child("Borrowing")
Stealing = Criminal_Law.add_child("Stealing")
Murder = Criminal_Law.add_child("Murder")
Man_Slaughter = Criminal_Law.add_child("Man_Slaughter")
Moving_Service = Contract_Law.add_child("Moving_Service")
Tax_Payment = Tax_Law.add_child("Tax_Payment")
Getting_Drivers_License = Administrative_Law.add_child("Getting_Drivers_License")
Income_Tax = Tax_Law.add_child("Income_Tax")
Building_Permission = Administrative_Law.add_child("Building_Permission")
Trademark = Intellectual_Property_Law.add_child("Trademark")
Copyright = Intellectual_Property_Law.add_child("Copyright")
Patent = Intellectual_Property_Law.add_child("Patent")
Design = Intellectual_Property_Law.add_child("Design")

#Test it! 
#Can be used with any of the instances.
Design.dfs_search()
