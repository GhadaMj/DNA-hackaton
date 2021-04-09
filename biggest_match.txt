from flask import Flask , render_template, request, url_for, flash, redirect
from werkzeug.exceptions import abort
import pandas as pd
import numpy as np
from flask import jsonify

from flask_cors import CORS

#import pickle
app = Flask(__name__)

cors = CORS(app)

app.config['SECRET_KEY'] = 'matching'




@app.route('/matching', methods=('GET', 'POST'))
def matching():
    project = request.args.get('project')
    users = request.args.get('users')
    response = {}
    #with open('questions_log.txt', 'a') as f:
    try:
        match=[]
        j=1
        for i in users:
            match.append({'id':i, 'match': round((len(set(users[i]['skills'])&set(projects['skills']))/len(projects['skills']) *100), 2)})
        match
    
        response ={"user"+str(j):users[i]['person_Id'], "match": percent, "skillInCommon": []}
        j=j+1
        
    except:
        response={}

    return jsonify(response), 200  




if __name__== "__main__":
	app.run(host='127.0.0.1',port=5001,debug=True)




