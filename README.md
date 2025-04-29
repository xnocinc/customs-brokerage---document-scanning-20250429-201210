# customs brokerage - document scanning

**Model Used:** `deepseek-r1:latest`

**Filename:** `CCI-Gemma3-reader`

**Prompt:**

```
Create a python program that using the Gemma 3 model to read scanned images of a PDF document and extract all data related to commercial customs invoices and add each element to a mysql database.
```

**Reasoning:**

```
Okay, so I need to write Python code that uses Gemma 3 to read scanned PDFs of commercial customs invoices and then add the extracted data to a MySQL database. Hmm, where do I start?

First, I remember that Gemma 3 is a tool for scanning and processing documents, including converting PDFs into structured data. So I'll need to install it first. I think using pip is the way to go, so I'll include the installation command for Gemma 3.

Next, once Gemma 3 is installed, I need to use its Python bindings. The main module for processing documents is probably `gemma3.process`, and maybe there's a specific function for invoices like `read_invoice`. So importing that makes sense.

Now, connecting to the MySQL database. I'll assume the user knows their credentials. Using the `mysql` Python library should work. I'll need to connect with the `pymysql` driver. So, import pymysql and establish a connection using the provided host, user, password, port, and database name.

Once connected, I need a function to extract data from an invoice. The steps here would be:
1. Read the PDF file using `DocumentReader`.
2. Process the document with `process_document`.
3. Extract specific fields like InvoiceNumber, DateOfIssue, etc., using the `extract` method.
4. Convert these extracted text values into appropriate data types (integers for numbers, dates as datetime objects) to ensure they're stored correctly in the database.

Putting this all together, I'll write a function called `process_invoice` that takes a file path and a cursor object. It will handle exceptions in case of errors during processing or extraction.

Then, another function `run Survey` might be needed if there's an associated form or survey with the invoice. This would call `process_survey` to get all necessary data.

Finally, I'll set up a loop that continuously reads new invoices from a directory. For each file, it will check if it ends with .pdf and then run the processing function. After processing, it commits the database changes.

I should make sure to include error handling so that if something goes wrong during processing or extraction, it doesn't crash the entire script but logs the issue instead.

Wait, I also need to import the necessary modules at the top. So, I'll list `import os`, `from gemma3.process import DocumentReader, process_document`, and then `import pymysql`.

Putting it all together, I think this structure should work. The code starts by installing Gemma 3 (even though in practice, you don't run this script from the command line with --install), imports everything needed, connects to the database, processes each PDF file, extracts data correctly, and commits changes.

I might have missed some steps or dependencies, but overall, that's the plan.
```