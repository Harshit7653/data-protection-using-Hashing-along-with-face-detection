import hashlib

yellow = '\033[93m'
lgreen = '\033[92m'
clear = '\033[0m'
bold = '\033[01m'
lightcyan = '\033[96m'
green= '\033[32m'
red = '\033[31m'

print (lightcyan+"""
   _______  ______  __________     ____  ____ _  __
  / ____\ \/ / __ )/ ____/ __ \   / __ )/ __ | |/ /
 / /     \  / __  / __/ / /_/ /  / __  / / / |   / 
/ /___   / / /_/ / /___/ _, _/  / /_/ / /_/ /   |  
\____/  /_/_____/_____/_/ |_|  /_____/\____/_/|_|       
""")
# Function to hash the string using MD5, SHA1, SHA256
def hash_string(string, hash_type):
    if hash_type == "md5":
        hash_object = hashlib.md5(string.encode())
        return hash_object.hexdigest()
    elif hash_type == "sha1":
        hash_object = hashlib.sha1(string.encode())
        return hash_object.hexdigest()
    elif hash_type == "sha256":
        hash_object = hashlib.sha256(string.encode())
        return hash_object.hexdigest()
    else:
        return "Invalid hash type"

while True:
    # Taking input from user
    
    option = input("Do you want to identify the hash type or encrypt the string? (identify/encrypt): ")

    if option == "identify":
        string = input(lgreen+"Enter the hash: ")
        # Identifying the hash type of the string
        if len(string) == 32:
            print(bold+"Hash type: MD5")
        elif len(string) == 40:
            print(bold+"Hash type: SHA1")
        elif len(string) == 64:
            print(bold+"Hash type: SHA256")
        else:
            print("Unable to identify hash type")
    elif option == "encrypt":
        string = input("Enter the string to be hashed: ")
        # Taking input from user for the encryption type
        encryption_type = input("Enter the encryption type (md5, sha1, sha256): ")

        # Calling the function to encrypt the string
        encrypted_string = hash_string(string, encryption_type)

        # Printing the encrypted string
        print("Encrypted string:",bold+ encrypted_string)
    else:
        print("Invalid option")

    # Asking user if they want to continue
    choice = input("Do you want to continue? (y/n): ")
    if choice.lower() == "n":
        break
