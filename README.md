# Single_ton_pattern_example
class Encapsulation:
    __instance = None  #######Singleton instance 

    def __init__(self, empId, empCode):
        if Encapsulation.__instance is not None:
            raise Exception("This class is a singleton! Use 'get_instance()' method instead.")
        else:
            self.empId = empId
            self.empCode = empCode
            Encapsulation.__instance = self

    @staticmethod
    def get_instance(empId=None, empCode=None):
        if Encapsulation.__instance is None:
            if empId is None or empCode is None:
                raise ValueError("Initial values for empId and empCode must be provided.")
            Encapsulation(empId, empCode)
            print("Access approved for the Employee details ...")
            Encapsulation.__instance.printing_empId()
            Encapsulation.__instance.printing_empCode()
        else:
            print("Not instantiable for second time: Only single time access is possible!")
        return Encapsulation.__instance

    def printing_empId(self):
        print(f"Employee id is: {self.empId}")

    def printing_empCode(self):
        print(f"Employee code is: {self.empCode}")

    # Getter and Setter for private attributes 
    def get_empId(self):
        return self.empId

    def set_empId(self, empId):
        self.empId = empId

    def get_empCode(self):
        return self.empCode

    def set_empCode(self, empCode):
        self.empCode = empCode


if __name__ == "__main__":
    empId = int(input("Enter emp id: "))
    empCode = input("Enter emp code: ")

    ######## Calling the singleton method to get the a single instance 
    Encapsulation.get_instance(empId, empCode)

    ######## Asking the user if they want to try again
    key = input("If you want to access again, enter 'yes' else 'no': ").lower()

    if key == 'yes':
        ######## Trying to create another instance (which is not possible)
        Encapsulation.get_instance(empId, empCode)
