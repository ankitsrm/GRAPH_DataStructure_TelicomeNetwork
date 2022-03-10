class TelecomeNetworkNode:
    def __init__(self,data):
        #In this method we are trying to create the graph
        self.data = data
        self.children = []
        self.parent = None

    def addChild(self, child):
        # For adding Child path to parent Path like A is the parent and there child will be B and C
        child.parent = self
        self.children.append(child)
    
def _writeToOutputPS2(insertingLine):
    #This method is use for printing output in outputPS2.txt
    try: 
        outputFile= open("outputPS2.txt","a+")
    except FileNotFoundError: 
        _writeToOutputPS2("outputPS2.txt file not found")
    except IOError:
        _writeToOutputPS2("outputPS2.txt file have no permission to read and write. ")
    if outputFile:
        outputFile.write("\n")
        outputFile.write(insertingLine)
    else:
        _writeToOutputPS2("outputfile variable is none.")

def readinputPS2():
    #This method is reading "InputPS2.txt" file for creating grap Breadth First Search  which uses Queue Data Structure for first in first out
    try:
        readinputPS2= open("inputPS2.txt", 'r') 
    except FileNotFoundError :
        _writeToOutputPS2("inputPS2.txt file not found")
    except IOError:
        _writeToOutputPS2("inputPS2.txt permission denied to read the file")
    # Reading inputPS2.txt file and below we are spliting lines 
    lineInputPS2= readinputPS2.read().splitlines()
    _telicomNetworkNode= TelecomeNetworkNode("Telecom_PATH_Costing")
    # Here we are trying to create Node --> "Telecom_Path_Costing"
    if readinputPS2:
        for inputLine in lineInputPS2:
            #In this for loop we are trying out to truncate the String input line and remove the "/" and perform the split method by which we get paths declation and there cost.
            data = inputLine.split("/", -1)
            path= data[0]+data[1]
            cost= int(data[2])   
            
            newNodeTelecome= TelecomeNetworkNode(path)
            newNodeTelecome.addChild(TelecomeNetworkNode(cost))
            _telicomNetworkNode.addChild(newNodeTelecome)
        # After that truncation of input line we are adding to the node and by this our graph can we conside 
    else: 
        _writeToOutputPS2("readPromptPS2 is null.")
    #This Method will return the Node.
    return _telicomNetworkNode

def readPromptPS2():
    #This Method will read the promptPS2.txt file.
    try:
        readPromptPS2 = open("promptPS2.txt", 'r')

    except FileNotFoundError :
        _writeToOutputPS2("promptPS2.txt file not found") 
    
    if readPromptPS2:
        linePromptPS2= readPromptPS2.read().splitlines()
        totalCost = 0

        
        mainNode = readinputPS2()
        if mainNode: 
            #Here we are calling readInputPS2.txt lines
            if linePromptPS2:
                for promptLine in linePromptPS2:
                    # It will read the each line of promptPS2.txt file and truncate the string to get the path which remove the ,.
                    
                    sep1 = promptLine.split(", ",-1)      
                    for str1 in sep1:
                        
                        forwardPath = str1[1]+str1[-2]
                        reversPath = str1[-2]+str1[1]
                        print(forwardPath , reversPath)
                        # In this we are trying to get the path name in forward as well as reverse direction which means if A to B is the direction then it will take a Forward as AB and BA as reverse. 
                        for pathNode in mainNode.children:
                        
                            for cost in pathNode.children:
                                if(pathNode.data == forwardPath or pathNode.data == reversPath):
                                    # If we get the path then we are adding the cost to toalCost which we defined as zero in first place
                                    totalCost = totalCost+cost.data
                _writeToOutputPS2("The offices can be connected as")
                _writeToOutputPS2(promptLine)
                _writeToOutputPS2("The minimum cost of connecting the offices is {}".format(totalCost))
            else:
                _writeToOutputPS2("In promptPS2.txt file there no lines to read.So we are terminating the process.")
        else:
            _writeToOutputPS2("Main node for the graph isnt created so we cant process it further. We are existing the process.")
    else: 
        _writeToOutputPS2("readPromptPS2 is Null so we cant proceed further")
    #Once the total cost we get then we are printing that to outputPS2.txt
    

if __name__ == "__main__" : 
    #readinputPS2()
    readPromptPS2()