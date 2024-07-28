import os  # Interacting with the file and directory operations.
import shutil  # Allows copying and moving files.
from datetime import datetime  # Provides classes for manipulating dates and times.
import logging  # Provides a flexible framework for emitting log messages, which is useful for tracking and debugging.

# Configure logging
logging.basicConfig(level=logging.DEBUG,  # Set the level to DEBUG to capture all messages
                    format='%(asctime)s - %(levelname)s - %(message)s',
                    datefmt='%Y-%m-%d %H:%M:%S')
# Path to the Downloads folder
downloads_path = os.path.expanduser('~/Downloads')

# Map file types to their respective folders
file_type_to_folder = {
    'Notes': ['.txt'],
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.tiff'],
    'Excel': ['.xls', '.xlsx', '.xlsm'],
    'CSV': ['.csv'],
    'PDF': ['.pdf']
}

# Create a folder if it doesn't exist
def create_folder_if_not_exists(folder_path):
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)

# Get the destination folder based on file type
def get_destination_folder(filename):
    for folder, extensions in file_type_to_folder.items():
        if any(filename.lower().endswith(ext) for ext in extensions):
            return folder
    return None

# Track created folders and organized files
created_folders = set()
organized_files = False

try:
    for filename in os.listdir(downloads_path):  # List all files in the Downloads directory.
        file_path = os.path.join(downloads_path, filename)
        if os.path.isfile(file_path):  # Process only files
            destination_folder = get_destination_folder(filename)
            
            if destination_folder:
                # Organize files by month-year of creation
                creation_time = os.path.getctime(file_path)
                date = datetime.fromtimestamp(creation_time)
                month_year_folder_path = os.path.join(downloads_path, date.strftime('%B_%Y'))

                # Ensure month-year and destination folders exist
                create_folder_if_not_exists(month_year_folder_path)
                created_folders.add(month_year_folder_path)

                destination_folder_path = os.path.join(month_year_folder_path, destination_folder)
                create_folder_if_not_exists(destination_folder_path)
                
                # Handle potential file name conflicts
                target_path = os.path.join(destination_folder_path, filename)
                if os.path.exists(target_path):
                    base, extension = os.path.splitext(filename)
                    counter = 1
                    while os.path.exists(target_path):
                        target_path = os.path.join(destination_folder_path, f"{base}_copy{counter}{extension}")
                        counter += 1

                # Move the file to the destination folder
                shutil.move(file_path, target_path)
                created_folders.add(destination_folder_path)
                organized_files = True
            else:
                logging.warning(f"File '{filename}' did not match any predefined folder categories.")

    # Log the results of the organization process
    if organized_files:
        logging.info('Files have been organized.')
        logging.info('Created folders:')
        for folder in created_folders:
            logging.info(folder)
    else:
        logging.info('No new files to organize.')
except Exception as e:
    logging.error(f'An error occurred: {e}')

