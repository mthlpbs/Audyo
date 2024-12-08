# Audyo

## Installation requirements:
		- Windows 7 or later
		- JDK 18 or later
		- ffmpeg (ffplay)

## Start workflow
```
	BEGIN
		// Check if the ".audisync" folder does not exist or if ".reset" file exists or if ".config" does not exist
		IF (".audisync" folder DOES NOT EXIST IN %USERPROFILE%) OR (".reset" file DOES EXIST IN %USERPROFILE%) OR
			(".audisync/.config" DOES NOT EXIST IN %USERPROFILE%) THEN
	  
			// Check if the ".reset" condition is true to overwrite ".audisync"
			IF (".reset" file EXISTS IN %USERPROFILE%) THEN
				OVERWRITE ".audisync" folder
			ELSE
				CREATE ".audisync" folder IN %USERPROFILE%
				CREATE ".config" file IN %USERPROFILE%/.audisync
				CREATE ".json" file IN %USERPROFILE%/.audisync
			ENDIF
			
			// Ask user for preferred music folder path
			INPUT user preferred music folder path       
			// If the user did not provide a path, set default music folder path
			IF user DID NOT PROVIDE a path THEN
				SET music folder path TO %USERPROFILE%/Music
			ELSE
				SET music folder path TO user input
			END IF
		END IF

		IF ".json" IS EMPTY THEN
			// Add song information to ".json" file (use doubly linked list)
			ADD song's information TO ".json" file
		ELSE
			// Load songs to program (use doubly linked list)
			LOAD songs FROM ".json" FILE INTO program
			
			FOR song IN music folder DO
				// If song name does not exist in the ".json" file, add it
				IF song name DOES NOT EXIST IN ".json" THEN
					ADD song's information TO ".json" file // (use doubly linked list)
				END IF
			END FOR
		END IF
		SHOW Home Window
	END
```

## CLI UI

### Home Screen
	
	```
		=======================================
			     AUDISYNC HOME
		=======================================
		[1] Create a Playlist
		[2] View Playlists
		[3] Delete a Playlist

		[4] Settings
		[5] Exit
		---------------------------------------
		Enter your choice:
		
	```
	
### Create Playlist
	
	```
		=======================================
			  CREATE NEW PLAYLIST
		=======================================
		Enter playlist name: __________________

		[0] Cancel
		---------------------------------------
		Press [Enter] to save the playlist.

	```
	
### View Playlist
	
	```
		=======================================
			     YOUR PLAYLISTS
		=======================================
		[1] Favourite
		[2] KPOP
		[3] Old Hits
		[4] LOFI

		[0] Back to Home
		---------------------------------------
		Select a playlist to play or manage: 

	```
	
### Playlist Details
	
	```
		=======================================
			    PLAYLIST: FAVOURITE
		=======================================
		[1] Play All Songs
		[2] Add Songs
		[3] Remove Songs
		[4] View Songs in Playlist
		[5] Rename Playlist

		[0] Back to Playlists
		---------------------------------------
		Enter your choice: 
		
	```
	
### Add song
	
	```
	
		=======================================
			     ADD SONGS
		=======================================
		Enter the path of the song to add:
		> _____________________________________

		[1] Add Another Song
		[0] Back to Playlist
		---------------------------------------
		Press [Enter] after entering the song path.

	```
	
### Settings
	
	```
		=======================================
			       SETTINGS
		=======================================
		[1] Change Default Music Folder
		[2] Reset Application
		[3] About

		[0] Back to Home
		---------------------------------------
		Enter your choice: 

	```
	
### Chnage Default Music Folder
	
	```
		=======================================
                  CHANGE DEFAULT MUSIC FOLDER
		=======================================
		Current folder: C:\Users\YourUser\Music
		Enter new folder path:
		> _____________________________________

		[0] Cancel
		---------------------------------------
		Press [Enter] to save changes.

	```
	
### About
	
	```
		
		=======================================
			     ABOUT AUDISYNC
		=======================================
		Version: 1.0.0
		Developer: Mithila Prabashwara
		Description:
		A CLI-based music manager with playlists
		powered by a doubly linked list data structure.

		[0] Back to Settings
		---------------------------------------
		Press [Enter] to return.
		
	```

	
