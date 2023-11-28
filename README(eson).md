**********************Subject: DT1
Assignment: LC1**********************************


****Software Architecture
 ********

**User Interface:**
•	Denotes the interface by which consumers engage with the system, as in the case of a web application.

Text Completion API:
•	An API that fulfils user interface requests for recommendations on text completion.
•	Facilitates interaction between the language model and the user interface.

Language Model: 
•	The fundamental element tasked with producing text completions.
•	It could be a sophisticated language model such as GPT-3 in this instance.

Database:
•	User-specific information is stored, including preferences, history, and suggestions.
•	To generate customised recommendations, the Text Completion API might engage in database interaction.

External Database:
•	The system may utilise external data sources, including context data, pre-trained models, or custom dictionaries, to improve text completion.

Flow:
•	Text completion requests are transmitted from the User Interface to the Text Completion API.
•	To generate suggestions, the Text Completion API communicates with the Language Model.
•	External data sources may be employed by the Language Model to provide context and information.
•	For presentation, the recommendations are returned to the user interface.
•	The storage and retrieval of user-specific data is an elective feature of the database.


**Text completion website (bubble)**
My App link : 
https://dt1-23-95608.bubbleapps.io/version-test

**Hugging Face API Key : ** 
•	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
•	Model : https://api-inference.huggingface.co/models/facebook/blenderbot-400M-distill

**Chatgpt script **: 
    <script>
        document.getElementById('chat_submit').addEventListener('click', async function () {
    // Get user input from the input field
    const userInput = document.getElementById('chat_input').value;

    // Display the user message in the output box
    displayMessage('User', userInput);

    // Clear the input field
    document.getElementById('chat_input').value = '';

    // Prepare the data for the API request
    const requestData = {
        inputs: {
            past_user_inputs: ["The purpose of the life is ?"],
            generated_responses: ["to be happy."],
            text: userInput
        }
    };

    try {
        // Make a POST request to the Hugging Face Inference API
        const response = await fetch('https://api-inference.huggingface.co/models/facebook/blenderbot-400M-distill', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer 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'
            },
            body: JSON.stringify(requestData)
        });

        // Parse the response as JSON
        const responseData = await response.json();

        // Display the bot's response in the output box
        displayMessage('Bot', responseData.generated_text);
    } catch (error) {
        console.error('Error:', error);
        // Handle errors, e.g., display an error message to the user
        displayMessage('Bot', 'Error occurred while fetching the response.');
    }
});

// Function to display messages in the output box
function displayMessage(sender, message) {
    const chatOutput = document.getElementById('chat_output');
    const currentContent = chatOutput.innerText;
    chatOutput.innerText = `${currentContent}${sender}: ${message}\n`;
}


    </script>






 



************Detail: ************
1.	Clone this repository locally on your machine.

•	I cloned this repository in the name of DT1-1 



2.	Read all the details provided to you this is pdf and on the README.md file of the repository you cloned. Draw the architecture diagram showing the system. [2points]

•	Done, Diagram is on the start page.


3.	Build the docker image locally [1 point]

•	Followed every step on https://docs.docker.com/get-started/02_our_app/

•	Created docker file and image in the name of image.



4.	Create a Docker Hub personal account (1 private image is free!) [1 point]
•	Created (account name : eson01)


5.	Push this image to your Docker Hub [1 point]
•	Changed contained name from image to eson01/image using cmd “docker tag image eson01/image”
•	Then pushed it to hub using “Push to hub” button


6.	Create a Hugging Face account and create an API Key [1 point]
•	Account has been created using GitHub account (eson01)
•	API key : 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


7.	Create a private Github repository called <firstname_lastname>-dt1-23 to version [1 point]

•	Private repository : DT1---LC1


8.	Login to your Google Cloud Platform account [1 point]

•	Done using google account. 

9.	Start a new virtual machine (VM) [1 point]

•	Select Your Project:
•	Navigate to Compute Engine:
•	Create a New VM Instance:
•	Configure Boot Disk:
•	Configure Networking:
•	Configure Management, Security, and Disks:
•	Click "Create":
•	Wait for the VM to Start:
•	Access the VM


10.	SSH into the virtual machine [1 point]
•	Debian OS was installed.
•	Click the "SSH" button next to the VM instance you want to access.
•	SSH Button
•	Used the Web-Based SSH Terminal to access VM 

11.	Install Docker on the virtual machine [1 point]
•	Docker is installed by instruction from https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-debian-10


12.	Pull the docker image you saved on Docker Hub [1 point]
•	“docker pull eson01/image” command is used to pull the image from my docker hub to VM 

13.	Run the image [1 point]
•	“docker run eson01/image” command is used to run the image

14.	Firewall the system so that only you can access the system [2 points]
•	Created.

15.	Create the frontend Bubble interface with the appropriate elements [2 points]
•	Created. https://dt1-23-95608.bubbleapps.io/version-test

16.	Write or have chatGPT generate some javascript code to make API calls to the
Docker Container on the VM (get app routes from the code in main.py) [2 points]

    <script>
        document.getElementById('chat_submit').addEventListener('click', async function () {
    // Get user input from the input field
    const userInput = document.getElementById('chat_input').value;

    // Display the user message in the output box
    displayMessage('User', userInput);

    // Clear the input field
    document.getElementById('chat_input').value = '';

    // Prepare the data for the API request
    const requestData = {
        inputs: {
            past_user_inputs: ["The purpose of the life is ?"],
            generated_responses: ["to be happy."],
            text: userInput
        }
    };

    try {
        // Make a POST request to the Hugging Face Inference API
        const response = await fetch('https://api-inference.huggingface.co/models/facebook/blenderbot-400M-distill', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer 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'
            },
            body: JSON.stringify(requestData)
        });

        // Parse the response as JSON
        const responseData = await response.json();

        // Display the bot's response in the output box
        displayMessage('Bot', responseData.generated_text);
    } catch (error) {
        console.error('Error:', error);
        // Handle errors, e.g., display an error message to the user
        displayMessage('Bot', 'Error occurred while fetching the response.');
    }
});

// Function to display messages in the output box
function displayMessage(sender, message) {
    const chatOutput = document.getElementById('chat_output');
    const currentContent = chatOutput.innerText;
    chatOutput.innerText = `${currentContent}${sender}: ${message}\n`;
}


    </script>












17.	Display API responses to the user in Bubble [2 points]
 


18.	After the system works, include Josh Levent, Siddhartha Singh in your firewall rules. [2 points]

•	Created rules with “All ports”

19.	Write all the details on the README-md file of your private github repository. [1point]
•	Done

20.	Add (as contributors) Josh Levent, Siddhartha Singh to the your Github Repository containing your solution [1 point]
•	Done
