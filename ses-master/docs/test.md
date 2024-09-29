# Transfer Management System

## Overview

The **Transfer Management System** is a PHP-based application designed to help companies manage large file transfers efficiently. It allows users to send and receive files securely, track their status, and ensure timely delivery. The system is designed to handle multiple transfers simultaneously, making it an ideal solution for businesses that require a robust file management system.

## Features

- **File Transfers**: Send large files to multiple recipients.
- **Transfer Tracking**: Monitor the status of each transfer in real time.
- **Expiration Management**: Set expiration dates for transfers to manage file availability.
- **Multiple Recipients**: Send files to multiple recipients with ease.
- **Custom Fields**: Support for additional custom metadata associated with each transfer.
- **Notifications**: Alert recipients when a transfer is sent or nearing expiration.

## Technologies Used

- **Backend**: PHP
- **Database**: MySQL
- **File Downloads**: aria2c (for efficient downloading)
- **Scripting**: Bash
- **Environment**: Nginx web server

## Database Schema

The application uses a MySQL database (`ses`) to store transfer and file information. The main tables include:

### Table: `transfers`

- **uuid** (CHAR(36)): Unique identifier for the transfer (UUID).
- **id** (VARCHAR(255)): Unique ID for the transfer.
- **to_email** (VARCHAR(255)): Recipient's email address.
- **from_email** (VARCHAR(255)): Sender's email address.
- **status** (VARCHAR(255)): Current status of the transfer.
- **expire_date** (BIGINT): Expiration date in Unix timestamp format.
- **is_expired** (BOOLEAN): Indicates if the transfer is expired.

### Table: `files`

- **uuid** (VARCHAR(255)): Unique identifier for the file (UUID).
- **transfer_id** (CHAR(255)): Foreign key referencing the `transfers` table.
- **filename** (VARCHAR(255)): Name of the file.
- **filesize** (BIGINT): Size of the file in bytes.
- **download_url** (VARCHAR(255)): URL to download the file.
- **file_status** (VARCHAR(255)): Status of the file (e.g., completed, pending).

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/transfer-management-system.git
   cd transfer-management-system

