<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PRIYANSHI KAUR'S SPACE 🚀</title>
    <style>
        body {
            background-image: url("https://i.imgur.com/PeB3ZTU.jpeg");
            background-size: cover;
            background-repeat: no-repeat;
            font-family: sans-serif;
            color: white;
            text-align: center;
            padding: 0;
            margin: 0;
            background-attachment: fixed;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }
        h1 {
            margin-top: 0;
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        input[type="text"] {
            width: 80%;
            padding: 10px;
            margin: 20px auto;
            border: none;
            border-radius: 5px;
            background-color: rgba(255, 255, 255, 0.2);
            color: white;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }
        button {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            background-color: #4CAF50;
            color: white;
            font-size: 1em;
            cursor: pointer;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }
        p {
            margin-top: 20px;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }
        .container {
            background-color: rgba(0, 0, 0, 0.5);
            padding: 20px;
            border-radius: 10px;
            backdrop-filter: blur(10px);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>PRIYANSHI KAUR'S SPACE 🚀</h1>
        <input type="text" id="videoLink" placeholder="Enter YouTube video link">
        <button onclick="downloadAudio()">Download</button>
        <p>Download Audio with ease!</p>
        <p>Remember to refresh the browser if you want to download again.</p>
    </div>

    <script>
        function downloadAudio() {
            const videoLink = document.getElementById("videoLink").value;
            // Your API key
            const apiKey = "AIzaSyB3BpB0pcTyvp27K2lLWVdd4aCOKID6gRU";

            // Use the YouTube Data API v3 to get video information
            fetch(`https://www.googleapis.com/youtube/v3/videos?part=snippet%2Csnippet%2CcontentDetails&id=${videoLink}&key=${apiKey}`)
                .then(response => response.json())
                .then(data => {
                    // Extract the audio stream URL (you'll need to figure out the correct format for this)
                    const audioUrl = data.items[0].contentDetails.audioUrl; // Placeholder - you'll need to find the actual audio URL

                    // Create a download link
                    const downloadLink = document.createElement("a");
                    downloadLink.href = audioUrl;
                    downloadLink.download = "audio.mp3"; // Set the file name
                    downloadLink.textContent = "Download Audio";

                    // Append the download link to the page
                    document.body.appendChild(downloadLink);
                })
                .catch(error => {
                    console.error("Error fetching video data:", error);
                    // Handle the error appropriately (e.g., display an error message)
                });
        }
    </script>
</body>
</html>