'''
Python script to detect emotion for the given text to analyze using Watson NLP service
'''
import json
import requests

def emotion_detector(text_to_analyze):
    '''
    Function that calls Watson NLP service and returns the response text
    '''
    url = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    headers = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    input_json = { "raw_document": { "text": text_to_analyze } }
    response = requests.post(url, json= input_json, headers= headers, timeout=5000)
    formatted_response = json.loads(response.text)
    emotion = formatted_response['emotionPredictions'][0]['emotion']
    res = {
        'anger': emotion['anger'],
        'disgust': emotion['disgust'],
        'fear': emotion['fear'],
        'joy': emotion['joy'],
        'sadness': emotion['sadness'],
        'dominant_emotion': max(emotion, key=emotion.get)
    }
    return res
