# YouTube Chat Extraction Example

This example notebook demonstrates how to extract live chat messages from YouTube videos using the `pytchat` library. Below is a step-by-step breakdown 
of each part of the code.

[Watch the Video!](https://www.youtube.com/watch?v=z0P4_NX_Icw)

1. **Import Libraries**
   ```python
   import pytchat
   import json
   ```

2. **Extract Chat Messages**
   - Initializes a file to store chat messages.
   - Creates a `pytchat` object for a specific YouTube video.
   - Iterates through live chat messages and writes them to a file.
   ```python
   # %%time
   f = open('mfPWbIcHtaM.txt', 'w')
   chat = pytchat.create(video_id="mfPWbIcHtaM")
   while chat.is_alive():
       for c in chat.get().items:
           obj = c.json()
           obj2 = json.loads(obj)
           f.write(str("{} {}: {}".format(obj2['author']['name'], obj2['datetime'], obj2['message']).encode('utf8')))
           f.write("\\n")
   f.close()
   ```

3. **Output Example**
   - Shows the structure of a chat message object.
   ```python
   obj2
   ```

4. **Another Chat Extraction Example**
   - Similar setup for a different YouTube video.
   - Filters messages by author.
   - Writes filtered messages to a file.
   ```python
   # %%time
   f = open('q3alUrfh6BI.txt', 'w')
   chat = pytchat.create(video_id="q3alUrfh6BI")
   while chat.is_alive():
       for c in chat.get().items:
           if 'Kyl' in c.json():
               obj = c.json()
               obj2 = json.loads(obj)
               print(obj2['author']['name'] + ': ' + obj2['message'])
           f.write(str("{}: {}".format(obj2['author']['name'], obj2['message']).encode('utf8')))
           f.write("\\n")
   f.close()
   ```