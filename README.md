# File Sharing Platform with Node.js and Express.js

In today's digital age, having a reliable file-sharing solution is essential for seamless collaboration and media distribution. This project uses **Node.js** and **Express.js** to build a robust file-sharing platform. The platform supports secure file uploads, optional password protection, and straightforward file downloads.

## Features

- **File Upload and Storage**: Handle file uploads using Multer, a middleware for handling `multipart/form-data`.
- **File Metadata**: Store information like original name, path, password (if any), and download count.
- **Password Protection**: Secure shared files with passwords using bcrypt.
- **Upload and Download Handling**: Routes for uploading files, downloading files, and password validation.

## Prerequisites

- **Node.js**
- **Express.js**
- **Mongoose** (for MongoDB integration)
- **Bcrypt** (for password encryption)
- **Multer** (for handling file uploads)
- **EJS** (for rendering HTML views)

## Installation

1. **Clone the Repository**:

   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Install Dependencies**:

   ```bash
   npm install bcrypt nodemon express multer dotenv ejs mongoose
   ```

3. **Set Up Environment Variables**:

   - Create a `.env` file and add your MongoDB connection URI and the desired port number:

   ```env
   MONGO=your_mongodb_uri
   PORT=3000
   ```

4. **Start the Server**:

   - Update `package.json` to include the start script:
     ```json
     "scripts": {
       "start": "nodemon server.js"
     }
     ```
   - Start the application using:

   ```bash
   npm start
   ```

5. **Access the Application**:

   - Visit [http://localhost:3000](http://localhost:3000) to use the file-sharing platform.

## Project Structure

```
.
|-- .env
|-- package.json
|-- server.js
|-- /models
    |-- File.js
|-- /views
    |-- index.ejs
    |-- download.ejs
|-- /uploads
```

## File Schema

The project uses **Mongoose** to define a schema for the files being uploaded:

```js
const mongoose = require("mongoose")

const File = new mongoose.Schema({
    path: {
        type: String,
        required: true
    },
    originalName: {
        type: String,
        required: true
    },
    password: String,
    downloadCount: {
        type: Number,
        required: true,
        default: 0
    }
})

module.exports = mongoose.model("File", File)
```

## How to Use

1. **Upload a File**:

   - Visit the home page and upload a file using the provided form.
   - You can optionally set a password to protect the file.

2. **Download a File**:

   - After uploading, a link is generated for sharing.
   - If the file is password-protected, the recipient will need to enter the password to download the file.

## Security Measures

- **Password Encryption**: File passwords are encrypted using **bcrypt** before storing.
- **Input Validation**: Validate user input to prevent malicious uploads and data corruption.
- **Error Handling**: Gracefully handle errors and invalid inputs to ensure a smooth user experience.

## Tech Stack

- **Node.js** and **Express.js** for server-side logic
- **Mongoose** for interacting with MongoDB
- **Multer** for file handling
- **EJS** for templating views

## Running Tests

To run the application from the root directory, use:

```bash
node server.js
```

## Author

- [Tanya Diit7](https://www.geeksforgeeks.org/author/tanyadiit7)

## License

This project is licensed under the MIT License.

## Acknowledgments

- Thanks to **GeeksforGeeks** for providing the sourcecode.

