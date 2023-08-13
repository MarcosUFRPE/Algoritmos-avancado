def recursividade_insertionsort(arrey, n=None):
    if n is None:
        n = len(arrey)
    
    if n <= 1:
        return
    
    recursividade_insertionsort(arrey, n-1)
    
    principal = arrey[n-1]
    z = n - 2
    
    while z >= 0 and arrey[z] > principal:
        arrey[z + 1] = arrey[z]
        z -= 1
    
    arrey[z + 1] = principal



def recursividade_selectionsort(arrey, n=None):
    if n is None:
        n = len(arrey)
    
    if n <= 1:
        return
    
    indeceMaximo = 0
    for i in range(1, n):
        if arrey[i] > arrey[indeceMaximo]:
            indeceMaximo = i
    
    arrey[n-1], arrey[indeceMaximo] = arrey[indeceMaximo], arrey[n-1]
    
    recursividade_selectionsort(arrey, n-1)


def insertionsort_iterativo(arrey):
    for i in range(1, len(arrey)):
        principal = arrey[i]
        j = i - 1 

        while j >= 0 and arrey[j] > principal:
            arrey[j + 1] = arrey[j]
            j -= 1
        arrey[j + 1] = principal

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.superior = None
    
    def append(self, data):
        new_node = Node(data)
        if not self.superior:
            self.superior = new_node
            return
        atual = self.superior
        while atual.next:
            atual = atual.next
        atual.next = new_node
    
    def display(self):
        atual = self.superior
        while atual:
            print(atual.data, end=" -> ")
            atual = atual.next
        print("None")

def selectionsort_linkedlist(linked_list):
    if linked_list.superior is None:
        return
    
    atual = linked_list.superior
    while atual:
        min_node = atual
        runner = atual.next
        while runner:
            if runner.data < min_node.data:
                min_node = runner
            runner = runner.next
        atual.data, min_node.data = min_node.data, atual.data
        atual = atual.next        
        
