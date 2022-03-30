# YouTube API v3
**By using the code below, you can *create* pickle files for Google API credentials :**

    import pickle
    from google_auth_oauthlib.flow import InstalledAppFlow
    
    client_secrets = 'CLIENTS_SECRET.json'
    scopes=["https://www.googleapis.com/auth/youtube.force-ssl"]
    credentials=InstalledAppFlow.from_client_secrets_file(client_secrets, scopes)
    credentials=credentials.run_console()
    
    with open('credentials.pickle', 'wb') as file:
	    pickle.dump(credentials, file)
	    file.close()

**By using the code below, you can *load* pickle files for Google API credentials :**

    import pickle
    
    with open('credentials.pickle', 'rb') as f:
	    credentials = pickle.load(f)
	    f.close()
**You can use the following function to add a comment on YouTube:**

    def addCommentOnYT(channelId, videoId, commentText):
	    res = youtube.commentThreads().insert(
		    part="snippet",
		    body={"snippet": {"channelId": channelId, "videoId": videoId,"topLevelComment": { "snippet": {"textOriginal": commentText}}}}).execute()
		return res

**You can use the following function to search for videos on YouTube:**

    def searchForVideos(keyword):
	    videos = youtube.search().list(part="snippet",
	    q=keyword, #Keyword e.g Minecraft
	    maxResults=10).execute()
	    return videos
