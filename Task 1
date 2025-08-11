from IPython.display import HTML

html_code = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Caesar Cipher</title>
    <!-- Tailwind CSS CDN for styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom styles for a cleaner look */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8;
            color: #333;
        }
        .container {
            max-width: 800px;
        }
        textarea, input[type="number"] {
            transition: all 0.2s;
        }
        textarea:focus, input[type="number"]:focus {
            outline: none;
            box-shadow: 0 0 0 3px rgba(66, 153, 225, 0.5); /* blue-500 with transparency */
        }
    </style>
</head>
<body class="p-4 md:p-8 flex items-center justify-center min-h-screen">
    <div class="container bg-white p-6 md:p-10 rounded-xl shadow-2xl w-full">
        <h1 class="text-3xl md:text-4xl font-bold text-center text-blue-800 mb-2">Caesar Cipher</h1>
        <p class="text-center text-gray-600 mb-8">Encrypt and decrypt messages by shifting letters in the alphabet.</p>

        <!-- Input Section -->
        <div class="mb-6">
            <label for="messageInput" class="block text-gray-700 font-semibold mb-2">Message:</label>
            <textarea id="messageInput" class="w-full p-4 border border-gray-300 rounded-lg focus:ring focus:ring-blue-500 focus:border-blue-500" rows="6" placeholder="Enter your message here..."></textarea>
        </div>

        <!-- Shift Value Input -->
        <div class="mb-8">
            <label for="shiftInput" class="block text-gray-700 font-semibold mb-2">Shift Value:</label>
            <input type="number" id="shiftInput" value="3" min="0" class="w-full p-3 border border-gray-300 rounded-lg focus:ring focus:ring-blue-500 focus:border-blue-500">
        </div>

        <!-- Buttons for Encrypt and Decrypt -->
        <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4 mb-8">
            <button id="encryptButton" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-6 rounded-lg transition-colors duration-200 shadow-md">
                Encrypt Message
            </button>
            <button id="decryptButton" class="flex-1 bg-gray-600 hover:bg-gray-700 text-white font-bold py-3 px-6 rounded-lg transition-colors duration-200 shadow-md">
                Decrypt Message
            </button>
        </div>

        <!-- Output Section -->
        <div>
            <label for="outputResult" class="block text-gray-700 font-semibold mb-2">Result:</label>
            <textarea id="outputResult" class="w-full p-4 border border-gray-300 rounded-lg bg-gray-100" rows="6" readonly placeholder="Encrypted or decrypted message will appear here..."></textarea>
        </div>
    </div>

    <script>
        // Get references to all the DOM elements we'll be interacting with
        const messageInput = document.getElementById('messageInput');
        const shiftInput = document.getElementById('shiftInput');
        const encryptButton = document.getElementById('encryptButton');
        const decryptButton = document.getElementById('decryptButton');
        const outputResult = document.getElementById('outputResult');

        /**
         * The core function to perform Caesar cipher operations.
         * It handles both encryption and decryption by adjusting the direction.
         * @param {string} text - The input message to process.
         * @param {number} shift - The number of places to shift each letter.
         * @param {number} direction - 1 for encryption, -1 for decryption.
         * @returns {string} The processed message.
         */
        const caesarCipher = (text, shift, direction) => {
            let result = '';
            // Modulo 26 ensures the shift value wraps around the alphabet.
            // For example, a shift of 27 is the same as a shift of 1.
            const adjustedShift = ((shift % 26) + 26) % 26;

            for (let i = 0; i < text.length; i++) {
                const char = text[i];
                let charCode = char.charCodeAt(0);

                // Check if the character is an uppercase letter (A-Z)
                if (charCode >= 65 && charCode <= 90) {
                    // Apply the shift and wrap around the alphabet (A-Z)
                    charCode = charCode + (adjustedShift * direction);
                    if (charCode > 90) {
                        charCode -= 26;
                    } else if (charCode < 65) {
                        charCode += 26;
                    }
                    result += String.fromCharCode(charCode);
                }
                // Check if the character is a lowercase letter (a-z)
                else if (charCode >= 97 && charCode <= 122) {
                    // Apply the shift and wrap around the alphabet (a-z)
                    charCode = charCode + (adjustedShift * direction);
                    if (charCode > 122) {
                        charCode -= 26;
                    } else if (charCode < 97) {
                        charCode += 26;
                    }
                    result += String.fromCharCode(charCode);
                }
                // If the character is not a letter, just append it to the result
                else {
                    result += char;
                }
            }
            return result;
        };

        // Event listener for the Encrypt button
        encryptButton.addEventListener('click', () => {
            const message = messageInput.value;
            const shift = parseInt(shiftInput.value, 10);
            if (isNaN(shift)) {
                outputResult.value = 'Please enter a valid number for the shift value.';
                return;
            }
            const encryptedText = caesarCipher(message, shift, 1);
            outputResult.value = encryptedText;
        });

        // Event listener for the Decrypt button
        decryptButton.addEventListener('click', () => {
            const message = messageInput.value;
            const shift = parseInt(shiftInput.value, 10);
            if (isNaN(shift)) {
                outputResult.value = 'Please enter a valid number for the shift value.';
                return;
            }
            const decryptedText = caesarCipher(message, shift, -1);
            outputResult.value = decryptedText;
        });
    </script>
</body>
</html>
"""

HTML(html_code)
