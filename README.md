using System;
using System.Text.RegularExpressions;
using System.Text.RegularExpressions;
using System.Speech.Synthesis;


class CybersecurityChatbot
{
    // Initialize Speech Synthesizer for text-to-speech functionality
    static SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer();

    // Entry point of the application
    static void Main()
    {
        // Initialize Speech Synthesizer
        speechSynthesizer.SetOutputToDefaultAudioDevice();

        // Display the ASCII art (the logo)
        DisplayAsciiArt();

        // Greet the user and ask for their name
        GreetUser();

        // Start the main chat loop where the bot listens to user input
        ChatLoop();
    }

    // Function to speak the message using the SpeechSynthesizer
    static void Speak(string message)
    {
        speechSynthesizer.Speak(message);
    } 

This C# code generates a simple text-to-speech chatbot for cybersecurity. The functions of each component are broken down as follows

 Speech Synthesizer: To enable the bot to communicate with the user, text must be transformed into speech using the SpeechSynthesizer class.

 The main() method greets the user, initializes the speech synthesizer, displays an ASCII art logo, and initiates the chat loop in order to set up the chatbot.

 The Speak() method uses a speech synthesizer to speak a message that is passed in as input.


 static void DisplayAsciiArt()
    {
        // Set the text color to cyan for the ASCII art
        Console.ForegroundColor = ConsoleColor.Cyan;

        // Output the ASCII art to the console using a verbatim string literal
        Console.WriteLine(@"
========================================================================================================================
+++++++++++++++++++++++++++++++++++++++++██████╗██╗   ██╗██████╗ ███████╗███████╗       +              +
+++++++++++++++++++++++++++++++++++++++++██╔════╝██║   ██║██╔══██╗██╔════╝██╔════╝   +      +    +
+++++++++++++++++++++++++++++++++++++++++██║     ██║   ██║██████╔╝███████╗███████╗+     +     +
+++++++++++++++++++++++++++++++++++++++++██║     ██║   ██║██╔═══╝ ╚════██║╚════██║+        +         +
+++++++++++++++++++++++++++++++++++++++++╚██████╗╚██████╔╝██║     ███████║███████║     +          + 
+++++++++++++++++++++++++++++++++++++++++╚═════╝ ╚═════╝ ╚═╝     ╚══════╝╚══════╝           
========================================================================================================================
");

        // Reset text color back to default
        Console.ResetColor();
    }

The task of displaying ASCII art in a particular color on the console falls to this function, DisplayAsciiArt().

 What it does is broken down as follows:
 Choose the Console as the text color. ConsoleColor = ForegroundColor. To make the ASCII graphics appear in cyan on the console, the Cyan; line sets the text color to cyan.

 The Console is the ASCII art display. A big block of ASCII art is printed to the console using the WriteLine() method.  A verbatim string literal (@"") is used to display the ASCII graphics, allowing the string to span numerous lines without requiring escape letters for line breaks.

 Reset Text Color: The text color is returned to the standard console color by calling the Console.ResetColor() method once the ASCII art has been displayed.


static void GreetUser()
    {
        // Ask the user for their name
        Console.Write("Hey! What's your name?: ");
        string name = Console.ReadLine()?.Trim();

        // Loop to ensure the name is not empty
        while (string.IsNullOrEmpty(name))
        {
            // Alert the user if the name is empty
            Console.ForegroundColor = ConsoleColor.Red;
            Console.WriteLine("Name cannot be empty. Please enter your name:");
            Console.ResetColor();
            name = Console.ReadLine()?.Trim();
        }

        // Greet the user with their name
        string greeting = $"Hello, {name}! Welcome to the Cybersecurity Awareness Bot.";
        Console.WriteLine(greeting);
        Speak(greeting);
    }

    // Function to handle the chat loop where the bot listens to user input
    static void ChatLoop()
    {
        // Continuously prompt the user for input until they type 'exit'
        while (true)
        {
            Console.Write("Ask me something about cybersecurity (or type 'exit' to quit): ");
            string input = Console.ReadLine()?.ToLower().Trim();

            // If the user types 'exit', break out of the loop and end the chat
            if (input == "exit")
            {
                string exitMessage = "Goodbye! Stay safe online.";
                Console.WriteLine(exitMessage);
                Speak(exitMessage);
                break;
            }

            // Process the user's input
            RespondToInput(input);
        }

GreetUser() and ChatLoop() are the two chatbot methods defined by this code.  Here is a brief description of each:

 WelcomeUser()
 Request the name of the user:  The user is prompted to enter their name.

 Verify the input:  It will keep asking until a legitimate name is entered if the user leaves the name blank.

 Greet the user: After the user enters a valid name, a message and an audible greeting are displayed.

 ChatLoop()
 Launch the conversation loop:  It keeps asking the user a cybersecurity-related inquiry.

 Exit condition: It exits the loop and bids the user farewell if they input "exit".

 Process user input: It uses a method (RespondToInput) to process and reply to the user's inquiry for any other input.


  // Function to respond to the user's input based on predefined queries
    static void RespondToInput(string input)
    {
        // Set the response color to yellow for better visibility
        Console.ForegroundColor = ConsoleColor.Yellow;

        // Declare the response
        string response;

        // Switch case to handle different topics or commands
        switch (input)
        {
            // If the user asks how the bot is doing, provide a friendly response
            case "how are you":
                response = "I'm just a bot, but I'm here to help you stay safe online!";
                break;

            // If the user asks about the bot's purpose, explain it
            case "what's your purpose":
                response = "I provide cybersecurity awareness to help you avoid online threats.";
                break;

            // If the user asks what topics they can inquire about, provide a list
            case "what can i ask you about":
                response = "You can ask me about password safety, phishing, and safe browsing.";
                break;

            // Respond with advice on password safety
            case "password safety":
                response = "Use strong, unique passwords for each account. Consider using a password manager.";
                break;

            // Respond with tips on recognizing phishing attempts
            case "phishing":
                response = "Be cautious of emails and messages asking for personal information. Always verify links.";
                break;

            // Respond with guidance on safe browsing
            case "safe browsing":
                response = "Avoid clicking on suspicious links and use a reputable security tool.";
                break;

            // If the input doesn't match any known query, ask the user to rephrase
            default:
                Console.ForegroundColor = ConsoleColor.Red;
                response = "I didn't quite understand that. Could you rephrase?";
                break;
        }

        // Output the response to the console and speak the response
        Console.WriteLine(response);
        Speak(response);

        // Reset text color
        Console.ResetColor();
    }
}


This part of the code is like the brain of the chatbot that gives answers when the user asks certain questions. Here's what happens:

Choosing a Response Color:
The chatbot sets the color of its responses to yellow, making them easier to notice on the screen.

Checking the User’s Question:
The chatbot then looks at the question the user asks. It’s like the chatbot has a list of questions it knows how to answer, and it checks the user’s input against this list.

What Happens for Each Question:

If the user asks "How are you?", the bot responds with something friendly like, "I'm just a bot, but I'm here to help you!"

If the question is about what the bot’s purpose is, it explains it’s there to help with cybersecurity.

If the user asks "What can I ask you about?", it gives a few examples like password safety, phishing, and safe browsing.

If they ask about something specific, like "phishing," the bot gives advice about how to spot phishing scams.

If It Doesn’t Understand:
If the bot doesn’t understand what the user is asking, it responds with a “Could you rephrase?” message in red, letting them know it didn’t catch the question.

Speaking and Showing the Answer:
Once the bot knows what to say, it shows the answer on the screen and also speaks it out loud using text-to-speech.

End of the Chat:
Finally, after giving the answer, it resets the text color to normal, so things look clean.

This is part 2 of my code the update.
and this is a overview of this code block 


using System.Collections.Generic;
using System.Speech.Synthesis;
using System.Text.RegularExpressions;

class CybersecurityChatbot
{
    static SpeechSynthesizer speechSynthesizer = new SpeechSynthesizer();

    // Memory for user information
    static string userName = "";
    static string userInterest = "";

    // Dictionary for keyword-based responses
    static Dictionary<string, List<string>> keywordResponses = new Dictionary<string, List<string>>()
    {
        { "password", new List<string> {
            "Use strong, unique passwords for each account.",
            "Avoid using personal details like birthdays in passwords.",
            "Consider using a password manager to keep your passwords safe." }
        },
        { "phishing", new List<string> {
            "Watch out for emails that ask for personal information.",
            "Phishing attempts often look like they come from trusted sources.",
            "Never click suspicious links or download unknown attachments." }
        },
        { "privacy", new List<string> {
            "Check the privacy settings on your social media accounts.",
            "Avoid oversharing personal information online.",
            "Use two-factor authentication to protect your privacy." }
        }
    };

    static void Main()
    {
        speechSynthesizer.SetOutputToDefaultAudioDevice();
        DisplayAsciiArt();
        GreetUser();
        ChatLoop();
    }

    static void Speak(string message)
    {
        speechSynthesizer.Speak(message);
    }

This code defines the initial setup of a cybersecurity chatbot that uses text-to-speech to talk to the user. It also includes a memory system for user details and a set of
predefined responses for common cybersecurity topics. This code sets up the core foundation of a cybersecurity chatbot that uses text-to-speech to communicate with users. It begins by initializing a SpeechSynthesizer to allow the bot to speak aloud, and it defines variables to store the user's name and interests for a more personalized experience. The bot is equipped with a dictionary that maps cybersecurity-related keywords (like "password", "phishing", and "privacy") to multiple helpful tips, enabling it to give varied advice depending on the topic the user mentions. When the program starts, it activates the speaker, displays an ASCII art logo, greets the user by asking for their name, and then launches into a chat loop where it listens for user input. The Speak method is used throughout to voice any text response, making the chatbot interactive and accessible.

 static void Speak(string message)
    {
        speechSynthesizer.Speak(message);
    }

    static void DisplayAsciiArt()
    {
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine(@"
========================================================================================================================
+++++++++++++++++++++++++++++++++++++++++██████╗██╗   ██╗██████╗ ███████╗███████╗       +              +
+++++++++++++++++++++++++++++++++++++++++██╔════╝██║   ██║██╔══██╗██╔════╝██╔════╝   +      +    +
+++++++++++++++++++++++++++++++++++++++++██║     ██║   ██║██████╔╝███████╗███████╗+     +     +
+++++++++++++++++++++++++++++++++++++++++██║     ██║   ██║██╔═══╝ ╚════██║╚════██║+        +         +
+++++++++++++++++++++++++++++++++++++++++╚██████╗╚██████╔╝██║     ███████║███████║     +          + 
+++++++++++++++++++++++++++++++++++++++++╚═════╝ ╚═════╝ ╚═╝     ╚══════╝╚══════╝           
========================================================================================================================
");
        Console.ResetColor();
    }

    static void GreetUser()
    {
        Console.Write("Hey! What's your name?: ");
        userName = Console.ReadLine()?.Trim();

        while (string.IsNullOrEmpty(userName))
        {
            Console.ForegroundColor = ConsoleColor.Red;
            Console.Write("Name cannot be empty. Please enter your name: ");
            Console.ResetColor();
            userName = Console.ReadLine()?.Trim();
        }

        string greeting = $"Hello, {userName}! Welcome to the Cybersecurity Awareness Bot.";
        Console.WriteLine(greeting);
        Speak(greeting);
    }

    static void ChatLoop()
    {
        Console.WriteLine("Ask me about cybersecurity (type 'exit' to quit):");

        while (true)
        {
            Console.ForegroundColor = ConsoleColor.White;
            Console.Write("\n> ");
            string input = Console.ReadLine()?.ToLower().Trim();

            if (input == "exit")
            {
                string goodbye = $"Goodbye, {userName}! Stay safe online.";
                Console.WriteLine(goodbye);
                Speak(goodbye);
                break;
            }

            HandleInput(input);
        }
    } 
    
This section of the code handles the user interface and interaction flow of the chatbot. The Speak method allows the chatbot to vocalize any message using text-to-speech. The DisplayAsciiArt method prints a stylized ASCII logo in cyan, giving the program a visually engaging introduction. The GreetUser method prompts the user to enter their name, ensures the input is not empty, and then welcomes the user with both a printed and spoken message, creating a friendly start to the conversation. Finally, the ChatLoop method keeps the chatbot running in a loop, continuously accepting user input. If the user types "exit", the loop breaks and the bot says goodbye. For all other inputs, the message is passed to HandleInput for processing. This part of the code sets the tone for user interaction and manages the ongoing conversation.

{
        Console.ForegroundColor = ConsoleColor.Yellow;

        // Detect sentiment and respond empathetically
        if (DetectSentiment(input, out string sentimentResponse))
        {
            Console.WriteLine(sentimentResponse);
            Speak(sentimentResponse);
            Console.ResetColor();
            return;
        }

        // Check for cybersecurity keywords
        foreach (var keyword in keywordResponses.Keys)
        {
            if (input.Contains(keyword))
            {
                if (keyword == "privacy" || keyword == "phishing" || keyword == "password")
                    userInterest = keyword;

                Random rand = new Random();
                string response = keywordResponses[keyword][rand.Next(keywordResponses[keyword].Count)];

                string finalResponse = userInterest == keyword
                    ? $"Since you're interested in {keyword}, here's a tip: {response}"
                    : response;

                Console.WriteLine(finalResponse);
                Speak(finalResponse);
                Console.ResetColor();
                return;
            }
        }

        // Show topics list
        if (input.Contains("what can i ask"))
        {
            string options = "You can ask me about password safety, phishing, privacy, and more!";
            Console.WriteLine(options);
            Speak(options);
            Console.ResetColor();
            return; // ✅ Prevents fallback from showing
        }

        // Remember user interest (flexible phrasing)
        Match match = Regex.Match(input, @"(?:i(?:'m| am)?\s*interested in|i like|i care about)\s+(\w+)");
        if (match.Success)
        {
            userInterest = match.Groups[1].Value;
            string rememberMsg = $"Got it! I’ll remember that you're interested in {userInterest}.";
            Console.WriteLine(rememberMsg);
            Speak(rememberMsg);
            Console.ResetColor();
            return;
        }

        // Default fallback
        string fallback = "I'm not sure I understand that. Could you rephrase or ask about a cybersecurity topic?";
        Console.ForegroundColor = ConsoleColor.Red;
        Console.WriteLine(fallback);
        Speak(fallback);
        Console.ResetColor();
    }

    static bool DetectSentiment(string input, out string response)
    {
        if (input.Contains("worried") || input.Contains("nervous") || input.Contains("scared"))
        {
            response = "It's completely understandable to feel that way. Cyber threats can be overwhelming. Let me help.";
            return true;
        }
        else if (input.Contains("curious") || input.Contains("interested") || input.Contains("excited"))
        {
            response = "That's great! Curiosity is key to learning more about cybersecurity. Ask me anything.";
            return true;
        }
        else if (input.Contains("frustrated") || input.Contains("annoyed") || input.Contains("tired"))
        {
            response = "Cybersecurity can feel overwhelming sometimes. I'm here to make it simpler.";
            return true;
        }

        response = "";
        return false;
    }
}

This part of the code handles how the chatbot understands and responds to user input by analyzing the text and determining the most appropriate reply. The HandleInput method first checks if the user expresses an emotion (like being worried, excited, or frustrated) using the DetectSentiment method, which returns a supportive message if a sentiment is detected. If no emotion is found, the method looks for known cybersecurity keywords such as "password", "phishing", or "privacy". If one is found, the bot selects a random tip from a predefined list and responds, sometimes adding a personal touch if the user has shown interest in that topic before. It also detects if the user asks a general question like "what can I ask", and responds with a list of available topics. Additionally, it uses pattern matching with regular expressions to understand phrases like “I’m interested in…” and stores the user’s interest for later responses. If none of these conditions are met, the bot gives a default message asking the user to rephrase. This section gives the chatbot the ability to respond intelligently, empathetically, and contextually based on the user's input.
