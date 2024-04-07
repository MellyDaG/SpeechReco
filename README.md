// Check for browser support
if (!('webkitSpeechRecognition' in window)) {
  alert('Your browser does not support speech recognition. Try Google Chrome.');
} else {
  var recognition = new webkitSpeechRecognition();
  recognition.continuous = true;
  recognition.interimResults = true;

  recognition.onstart = function() {
    console.log('Speech recognition started. Start speaking.');
  };

  recognition.onerror = function(event) {
    console.error('Speech recognition error detected: ' + event.error);
  };

  recognition.onend = function() {
    console.log('Speech recognition ended.');
  };

  recognition.onresult = function(event) {
    var transcript = '';
    for (var i = event.resultIndex; i < event.results.length; ++i) {
      transcript += event.results[i][0].transcript;
    }
    document.getElementById('transcript').textContent = transcript;
  };

  // Start recognition
  recognition.start();
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Speech Recognition Example</title>
</head>
<body>
    <h1>Speech Recognition Demo</h1>
    <p id="transcript">Speak something...</p>
    <script src="speechRecognition.js"></script>
</body>
</html>
