"""A video player class."""

from .video_library import VideoLibrary
import random

class VideoPlayer:
    """A class used to represent a Video Player."""
    playing_id = []
    pause_id = []

    def __init__(self):
        self._video_library = VideoLibrary()

    def number_of_videos(self):
        num_videos = len(self._video_library.get_all_videos())
        print(f"{num_videos} videos in the library")

    def show_all_videos(self):
        show_videos = self._video_library.get_all_videos()  #Returns all videos
        videos_list = []
        for video in show_videos:
            video_tags = str(video.tags)
            video_tags = video_tags.replace("(","")
            video_tags = video_tags.replace(")", "")
            video_tags = video_tags.replace(",", "")
            video_tags = video_tags.replace("'", "")
            #print(video_tags)
            videos_list.append([video.title,video.video_id,video_tags])
        sorted_videos = sorted(videos_list)
        print("Here's a list of all available videos:")
        for final_show_videos in sorted_videos:
            print(" ",final_show_videos[0],"({})".format(final_show_videos[1]),"[{}]".format(final_show_videos[2]))


    def play_video(self, video_id):
        show_videos = self._video_library.get_all_videos() #Plays the respective video.
        videos_list = []
        for video in show_videos:
            videos_list.append([video.title,video.video_id])
        try:
            video_index = [x[1] for x in videos_list].index(video_id)
            if len(self.playing_id)>0:
                print("Stopping video: {}".format(videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0]))
                self.playing_id = []
                self.pause_id = []
            else:
                try:
                    trial = [x[1] for x in videos_list].index(video_id)
                    self.playing_id.append(video_id)
                except:
                    pass
            print("Playing video: ",videos_list[video_index][0])
            self.playing_id.append(video_id)
            self.pause_id = []
        except:
            print("Cannot play video: Video does not exist")




    def stop_video(self):
        show_videos = self._video_library.get_all_videos()  #Stops the current video.
        videos_list = []
        for video in show_videos:
            videos_list.append([video.title, video.video_id])
        if len(self.playing_id)>0:
            print("Stopping video: {}".format(videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0]))
            self.playing_id = []
            self.pause_id = []
        else:
            print("Cannot stop video: No video is currently playing")

    def play_random_video(self):
        show_videos = self._video_library.get_all_videos()  # Plays a random video from the video library.
        random_index = random.randint(0, len(show_videos))
        videos_list = []
        for video in show_videos:
            videos_list.append([video.title, video.video_id])
        rd_vid_id = videos_list[random_index][1]
        self.play_video(rd_vid_id)

    def pause_video(self):
        show_videos = self._video_library.get_all_videos() #Pauses the current video.
        videos_list = []
        for video in show_videos:
            videos_list.append([video.title, video.video_id])
        if len(self.playing_id)>0:
            if len(self.pause_id)>0:
                print("Video already paused: {}".format(videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0]))
            else:
                print("Pausing video: {}".format(videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0]))
                self.pause_id.append(self.playing_id[0])
        else:
            print("Cannot stop video: No video is currently playing")

    def continue_video(self):
        show_videos = self._video_library.get_all_videos() #Resumes playing the current video.
        videos_list = []
        for video in show_videos:
            videos_list.append([video.title, video.video_id])
        if len(self.playing_id) > 0:
            if len(self.pause_id) > 0:
                print("Continuing video: {}".format(
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0]))
                self.pause_id = []
            else:
                print("Cannot continue video: Video is not paused")
        else:
            print("Cannot continue video: No video is currently playing")

    def show_playing(self):
        show_videos = self._video_library.get_all_videos() #Displays video currently playing.
        videos_list = []
        for video in show_videos:
            video_tags = str(video.tags)
            video_tags = video_tags.replace("(", "")
            video_tags = video_tags.replace(")", "")
            video_tags = video_tags.replace(",", "")
            video_tags = video_tags.replace("'", "")
            videos_list.append([video.title, video.video_id, video_tags])
        if len(self.playing_id) > 0:
            if len(self.pause_id) > 0:
                print("Currently playing: {} ({}) [{}] - PAUSED".format(
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0],
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][1],
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][2]))
            else:
                print("Currently playing: {} ({}) [{}]".format(
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][0],
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][1],
                    videos_list[[x[1] for x in videos_list].index(self.playing_id[0])][2]))
        else:
            print("No video is currently playing")
