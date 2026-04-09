''' 
Application to run emotion detector over Flask channel
'''
from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask('Emotion Detection')

@app.route("/emotionDetector")
def emotion_analyzer():
    ''' 
    function calling the emotion detector utility
    '''
    input_text = request.args.get('textToAnalyze')
    response = emotion_detector(input_text)

    return ( f"For the given statement, the system response is "
    f"'anger': {response['anger']}, "
    f"'disgust': {response['disgust']}, "
    f"'fear': {response['fear']}, "
    f"'joy': {response['joy']} and "
    f"'sadness': {response['sadness']}. "
    f"The dominant emotion is {response['dominant_emotion']}."
    )
@app.route("/")
def render_index_page():
    ''' 
    Function initiates the rendering of the main page
    '''
    return render_template('index.html')

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)
