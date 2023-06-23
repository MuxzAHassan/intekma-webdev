
# File Management System Design

## Database Design

### Entity Relation Diagram for File Management System

![Entity Relation Diagram][ERD.jpg]

### Relationships

- Each **User** can have multiple **Files** and **Folders**.
- Each **File** belongs to a **User** who uploaded it.
- Each **Folder** can have multiple **Files** and **Folders** as its children.
- Each **Folder** has a parent **Folder**(except for the root folder)
- Each **Folder** can be mapped to multiple Users through the **Folder-User Mapping** table.

## System Process Flow

1. User Registration and Login:
    - Users can register by providing their username, password, and email.
    - Registered users can log in using their credentials.

2. Uploading Files:
    - Authenticated users can upload files.
    - The system saves the file with a unique file_id and stores it in the designated file_path.
    - The file record is created in the **Files** table, associating it with the user who uploaded it.
    - The user can specify if the file should be available to all users or only selected users.

3. Creating Folders:
    - Authenticated users can create folders.
    - The folder record is created in the **Folders** table, associating it with the user who created it.
    - The folder can be assigned a parent folder(except for the root folder).

4. Managing File/Folder Visibility:
    - Users can set the visibility of files/folders as public or private.
    - If a file/folder is marked public, it will be accessible to all users.
    - If a file/folder is marked private, the user can specify which users have access by adding them to the **Folder-User Mapping** table.

5. Browsing and Accessing Files/Folders:
    - Users can browse their own files/folders and view the files/folders available to them based on the permissions set by other users.
    - The system retrieves and displays the appropriate files/folders based on the user's access rights.

6. Nested Folders:
    - Users can create an unlimited level of folders within folders.
    - Each folder is associated with its parent folder through the parent_folder_id, forming a hierarchical structure.

[def]: ERD.jpg
[ERD.jpg]: /ERD.jpg