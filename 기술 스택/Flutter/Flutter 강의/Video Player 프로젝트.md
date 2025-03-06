---
설명: "[video_player플러그인, Stack, EventListener, didUpdateWidget]"
상위 항목:
  - "[[인프런 강의]]"
하위 항목:
  - "[[Gradient 집어넣기]]"
---
### textStyle.copyWith()

> [!important] 공통된 속성을 textStyle 이라는 객체로 정리했을때 공통 속성 외에 특별한 속성을 추가하고 싶다면
> 
> `.copyWith()` 내부에 적어주면 된다

  

### home_screen.dart

- 코드
    
    ```Dart
    <pubspec.yaml>
      flutter_lints: ^3.0.0
      video_player: ^2.8.2
      image_picker: ^1.0.7
    ```
    
    ```Dart
    import 'package:flutter/cupertino.dart';
    import 'package:flutter/material.dart';
    import 'package:flutter/widgets.dart';
    import 'package:image_picker/image_picker.dart';
    import 'package:video_player/video_player.dart';
    import 'dart:io';
    
    class HomeScreen extends StatefulWidget {
      const HomeScreen({super.key});
    
      @override
      State<HomeScreen> createState() => _HomeScreenState();
    }
    
    class _HomeScreenState extends State<HomeScreen> {
      XFile? video;
    
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          backgroundColor: Colors.black,
          body: video != null
              ? _VideoPlayer(
                  video: video!,
                  onAnotherVideoPicked: onLogoTapped,
                )
              : _VideoSelector(onLogoTapped: onLogoTapped),
        );
      }
    
      onLogoTapped() async {
        final video = await ImagePicker().pickVideo(
          source: ImageSource.gallery,
        );
        setState(() {
          this.video = video;
        });
      }
    }
    
    class _VideoSelector extends StatelessWidget {
      final VoidCallback onLogoTapped;
    
      const _VideoSelector({super.key, required this.onLogoTapped});
    
      @override
      Widget build(BuildContext context) {
        return Container(
          decoration: BoxDecoration(
            gradient: LinearGradient(
              begin: Alignment.topCenter,
              end: Alignment.bottomCenter,
              colors: [
                Color(0xFF2A3A7C),
                Color(0xFF000118),
              ],
            ),
          ),
          width: double.infinity,
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              _Logo(onTap: onLogoTapped),
              SizedBox(height: 28),
              _Title(),
            ],
          ),
        );
      }
    }
    
    class _Logo extends StatelessWidget {
      final VoidCallback onTap;
    
      const _Logo({super.key, required this.onTap});
    
      @override
      Widget build(BuildContext context) {
        return GestureDetector(
          onTap: onTap,
          child: Image.asset(
            'asset/image/logo.png',
          ),
        );
      }
    }
    
    class _Title extends StatelessWidget {
      const _Title({super.key});
    
      @override
      Widget build(BuildContext context) {
        final textStyle = TextStyle(
          color: Colors.white,
          fontSize: 32,
          fontWeight: FontWeight.w300,
        );
    
        return Row(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'VIDEO',
              style: textStyle,
            ),
            Text(
              'PLAYER',
              style: textStyle.copyWith(
                fontWeight: FontWeight.w700,
              ),
            ),
          ],
        );
      }
    }
    
    class _VideoPlayer extends StatefulWidget {
      final XFile video;
      final VoidCallback onAnotherVideoPicked;
    
      const _VideoPlayer({
        super.key,
        required this.video,
        required this.onAnotherVideoPicked,
      });
    
      @override
      State<_VideoPlayer> createState() => _VideoPlayerState();
    }
    
    class _VideoPlayerState extends State<_VideoPlayer> {
      /// late - 지금 초기화하지 않겠다는 뜻, 사용되기 직전에는 무조건 해줄거라는 약속
      late VideoPlayerController videoPlayerController;
      bool showIcons = true;
    
      @override
      void initState() {
        super.initState();
        initializeController();
      }
    
      @override
      didUpdateWidget(covariant _VideoPlayer oldWidget) {
        super.didUpdateWidget(oldWidget);
    
        if (oldWidget.video.path != widget.video.path) {
          initializeController();
        }
      }
    
      initializeController() async {
        videoPlayerController = VideoPlayerController.file(
          File(
            widget.video.path,
          ),
        );
    
        await videoPlayerController.initialize();
    
        // videocontroller에 변경이 생길때마다 콜백함수를 실행
        videoPlayerController.addListener(() {
          setState(() {});
        });
      }
    
      @override
      Widget build(BuildContext context) {
        return GestureDetector(
          onTap: () {
            setState(() {
              showIcons = !showIcons;
            });
          },
          child: Center(
            child: AspectRatio(
              aspectRatio: videoPlayerController.value.aspectRatio,
              child: Stack(
                /// Stack 안에 넣은 순서대로 위로 올라옴
                children: [
                  VideoPlayer(videoPlayerController),
                  if (showIcons)
                    Container(
                      width: double.infinity,
                      height: double.infinity,
                      color: Colors.black.withOpacity(0.5),
                    ),
                  if (showIcons)
                    _PlayButtons(
                      onForwardPressed: onForwardPressed,
                      onPausePressed: onPausePressed,
                      onReversePressed: onReversePressed,
                      isPlaying: videoPlayerController.value.isPlaying,
                    ),
                  if (showIcons)
                    _Bottom(
                      position: videoPlayerController.value.position,
                      maxPosition: videoPlayerController.value.duration,
                      onSliderChanged: onSliderChanged,
                    ),
                  if (showIcons)
                    _PickAnotherVideo(
                      onPressed: widget.onAnotherVideoPicked,
                    ),
                ],
              ),
            ),
          ),
        );
      }
    
      onSliderChanged(double val) {
        final position = Duration(seconds: val.toInt());
        videoPlayerController.seekTo(position);
      }
    
      onReversePressed() {
        final currentPosition = videoPlayerController.value.position;
        Duration position = Duration();
    
        /// 3초 초과 진행됐으면 -3초, 그외에는 0으로 초기화
        if (currentPosition.inSeconds > 3) {
          position = currentPosition - Duration(seconds: 3);
        }
    
        videoPlayerController.seekTo(position);
      }
    
      onPausePressed() {
        if (videoPlayerController.value.isPlaying) {
          videoPlayerController.pause();
        } else {
          videoPlayerController.play();
        }
        setState(() {});
      }
    
      onForwardPressed() {
        final maxPosition = videoPlayerController.value.duration;
        final currentPosition = videoPlayerController.value.position;
        Duration position = maxPosition;
    
        /// 영상길이 마지막 3초 이내면 마지막으로, 그외에는 3초 씩 추가
        if ((maxPosition - Duration(seconds: 3)).inSeconds >
            currentPosition.inSeconds) {
          position = currentPosition + Duration(seconds: 3);
        }
    
        videoPlayerController.seekTo(position);
      }
    }
    
    class _PlayButtons extends StatelessWidget {
      final VoidCallback onReversePressed;
      final VoidCallback onPausePressed;
      final VoidCallback onForwardPressed;
      final bool isPlaying;
    
      const _PlayButtons(
          {super.key,
          required this.onForwardPressed,
          required this.onPausePressed,
          required this.onReversePressed,
          required this.isPlaying});
    
      @override
      Widget build(BuildContext context) {
        return Center(
          child: Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: [
              IconButton(
                color: Colors.white,
                onPressed: onReversePressed,
                icon: Icon(Icons.rotate_left),
              ),
              IconButton(
                color: Colors.white,
                onPressed: onPausePressed,
                icon: Icon(isPlaying ? Icons.pause : Icons.play_arrow),
              ),
              IconButton(
                color: Colors.white,
                onPressed: onForwardPressed,
                icon: Icon(Icons.rotate_right),
              ),
            ],
          ),
        );
      }
    }
    
    class _Bottom extends StatelessWidget {
      final Duration position;
      final Duration maxPosition;
      final ValueChanged<double> onSliderChanged;
    
      const _Bottom({
        super.key,
        required this.maxPosition,
        required this.position,
        required this.onSliderChanged,
      });
    
      @override
      Widget build(BuildContext context) {
        return Positioned(
          bottom: 0,
          left: 0,
          right: 0,
          child: Padding(
            padding: const EdgeInsets.symmetric(horizontal: 8.0),
            child: Row(children: [
              Text(
                '${position.inMinutes.toString().padLeft(2, '0')}'
                ':${(position.inSeconds % 60).toString().padLeft(2, '0')}',
                style: TextStyle(
                  color: Colors.white,
                ),
              ),
              Expanded(
                child: Slider(
                  max: maxPosition.inSeconds.toDouble(),
                  value: position.inSeconds.toDouble(),
                  onChanged: onSliderChanged,
                ),
              ),
              Text(
                '${maxPosition.inMinutes.toString().padLeft(2, '0')}'
                ':${(maxPosition.inSeconds % 60).toString().padLeft(2, '0')}',
                style: TextStyle(
                  color: Colors.white,
                ),
              ),
            ]),
          ),
        );
      }
    }
    
    class _PickAnotherVideo extends StatelessWidget {
      final VoidCallback onPressed;
    
      const _PickAnotherVideo({super.key, required this.onPressed});
    
      @override
      Widget build(BuildContext context) {
        return Positioned(
          right: 0,
          child: IconButton(
            color: Colors.white,
            onPressed: onPressed,
            icon: Icon(Icons.photo_camera_back),
          ),
        );
      }
    }
    ```