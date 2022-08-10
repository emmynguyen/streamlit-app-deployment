# Deployment Option #1: localhost
## Reference
[Official Streamlit Documentation](https://docs.streamlit.io/library/get-started/main-concepts)

## Walkthrough
1. Using Visual Studio Code or an IDE of your choice, create a single page or multipage streamlit application.
2. Create a requirements.txt file where "streamlit==1.11.1" is included.
3. In Visual Studio Code, click on "Terminal" and then select "New Terminal".
4. In the terminal window, ensure that you are either using zsh (MacOS) or Command Prompt (Windows).
5. Ensure that you are in the correct directory path before continuining.
6. Go ahead and create a virtual environment by leveraging python's venv capability. 
```
python -m venv venv
```
7. Activate the virtual environment that was just created. </br>
For Linux:
```
source ./venv/bin/activate
```
For Windows:
```
venv\Scripts\activate
```
8. Install the requirements.
```
python -m pip install -r requirements.txt
```
9. Run the following command:
If app is in the root directory:
```
streamlit run app.py
```
If app is in a folder rather than the root directory:
```
streamlit run folder/app.py
```
10. Once the app is running, you will be provided with a local URL and a network URL. You will either be redirected to a new tab with the local URL or you can copy/paste the local URL into a browser window of your choice. 
11. At this point, you should be able to view your application and interact with it as intended.