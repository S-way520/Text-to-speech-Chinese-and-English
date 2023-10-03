# Text-to-speech-Chinese-and-English
SwiftUI
# The first part
![IMG_0940](https://github.com/S-way520/Text-to-speech-Chinese-and-English/assets/95877651/3ed76397-1ac9-4ad7-81c2-ae247e67608b)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView(TextSay: "物体的空间位置随时间的变化，是自然界中最简单、最基本的运动形态， 叫作机械运动 (mechanical motion)。")
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import AVFoundation
struct ContentView: View {
    let speaker = AVSpeechSynthesizer()
    @State var TextSay: String
    var utterance: AVSpeechUtterance {
        let utterance = AVSpeechUtterance(string: TextSay)
        utterance.voice = AVSpeechSynthesisVoice(language: "zh-CN")
        utterance.voice = AVSpeechSynthesisVoice(identifier: "com.apple.ttsbundle.siri_male_zh-CN_compact")//Male voice
        return utterance
    }
    var body: some View {
        HStack {
            TextEditor(text: $TextSay)
                .multilineTextAlignment(.leading)
                .padding(10)
                .textFieldStyle(RoundedBorderTextFieldStyle())
                .lineSpacing(10.0)
        }
        Button(action: {
            self.playSpeech()
        }) {
            Image(systemName: "play.circle")
                .resizable()
                .frame(width: 50, height: 50)
                .aspectRatio(contentMode: .fit)
                .accentColor(.green)
        }
        .padding(20)
    }
    func playSpeech() {
        self.speaker.speak(self.utterance)
    }
}
```
