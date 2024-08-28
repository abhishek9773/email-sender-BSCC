# Email-Sender-BSCC

**Email-Sender-BSCC** is a Jupyter Notebook-based project designed to automate sending personalized emails to multiple educational institutions. The notebook reads and processes CSV files containing institution data, filters based on accreditation validity, and sends customized emails.

## Features

- **CSV Data Processing:** Reads multiple CSV files from a specified directory and merges them into a single DataFrame.
- **Date Filtering:** Filters rows based on accreditation validity, targeting institutions with accreditation valid until a specific year.
- **Automated Email Sending:** Sends personalized emails to each filtered institution using SMTP.
- **Logging:** Maintains logs of successfully sent emails and any errors encountered during the process.

## Prerequisites

Before running the notebook, ensure you have the following installed:

- Python 3.x
- Jupyter Notebook (`pip install notebook`)
- Pandas library (`pip install pandas`)
- SMTPLib and email libraries (included with Python's standard library)

## Setup Instructions

### Step 1: Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/your-username/email-sender-BSCC.git
cd email-sender-BSCC
```

### Step 2: Install Required Packages

Install the required Python packages:

```bash
pip install pandas notebook
```

### Step 3: Prepare Your CSV Files

Ensure your CSV files are stored in the `college_data` directory. This directory should be at the root level of the project. Each CSV file should have the following columns:

- `Name of the College/Institution`: Name of the college or institution.
- `Institute Email`: Email address of the institution.
- `Accreditation Valid Upto`: Date indicating how long the institution's accreditation is valid.

### Step 4: Update Email Credentials

Open the `email_sender.ipynb` notebook and update the following cells with your email credentials:

```python
# Email credentials
your_email = 'Enter_your_email'
your_password = 'Enter_your_password'
```

### Step 5: Customize the Email Content

Update the email content in the `email_template` variable. For example:

```python
# Email content
email_template = """
Dear Principal Sir/Madam,

I hope this email finds you well. My name is [Your Name], and I am from [Your Location]. I am writing to inquire about the possibility of securing admission to {college_name}, particularly for the [Your Program] program. I am facing significant financial challenges and seek your guidance on how I can overcome these obstacles to pursue my education.

[Your additional content here]

Sincerely,
[Your Name]
LinkedIn Profile - [Your LinkedIn Profile URL]
Resume - [Your Resume URL]
Mobile No - [Your Mobile Number]
"""
```

Replace the placeholder text with your actual details.

## Usage

1. **Open Jupyter Notebook**: Navigate to the project directory and start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

2. **Open `email_sender.ipynb`**: Open the `email_sender.ipynb` notebook in Jupyter Notebook.

3. **Run the Notebook**: Execute each cell in the notebook sequentially. The script will:

   - Load and merge all CSV files from the `college_data` directory.
   - Filter institutions based on accreditation validity.
   - Send personalized emails to each institution.
   - Log successfully sent emails in `sent_emails_log.txt`.
   - Log any errors in `error_log.txt`.

### Customization

- **Filter Year:** To change the year for filtering institutions based on accreditation validity, modify this line in the notebook:

  ```python
  filtered_df = df[df['Accreditation Valid Upto'].dt.year >= 2027]
  ```

  Replace `2027` with your desired year. Only institutions with accreditation valid until that year or later will be considered for email sending.

- **Email Server Settings:** By default, the script uses Gmail's SMTP server. If you want to use a different email service, update the SMTP server and port settings accordingly:

  ```python
  server = smtplib.SMTP('smtp.gmail.com', 587)
  ```

- **Email Template:** The email template can be fully customized to suit different needs. Use `{college_name}` as a placeholder to insert the institution's name dynamically.

## Viewing Logs

- **Sent Emails Log (`sent_emails_log.txt`)**: This file records the email addresses to which emails have been successfully sent. You can review this file to see which emails were processed.
- **Error Log (`error_log.txt`)**: This file captures any errors encountered during the email sending process. Review this file to troubleshoot any issues with sending emails.

## Contribution

Contributions are welcome! Please feel free to submit a Pull Request if you have any improvements or bug fixes.

---
