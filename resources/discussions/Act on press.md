Link: https://x.com/ID_AA_Carmack/status/1787850053912064005
Author: [[John Carmack]]

## takeaways

- many UI interactions are a combination of pressing and releasing
- snappy experiences come from 'doing the thing' on press, not release
## transcript

> Act on press 
> 
> This is a UI design hill I will die on, and it dismays me how often and hard I have had to fight for it. 
> 
> Almost all interaction methods have a “press” and “release” event associated with them. Whenever possible, you should “do the thing” when you get the press event instead of waiting for the release event, because it makes the interaction feel substantially more responsive, and it reduces user errors by not allowing the focus to slide out of the hot box between press and release. 
> 
> Even a “ballistic tap”, where your finger is intentionally bouncing off the button or touch surface, involves several tens of milliseconds delay between the press and release, and most button presses have well over a hundred ms dwell time. There is a delight in interfaces that feel like they respond instantly to your wishes, and the benefit to every single user is often more important than additional niche features. 
> 
> Game developers, with simple UI toolkits, tend to get this right more often, but “sophisticated” app designers will often fight hard against it because it is mostly incompatible with options like interactive touch scrolling views, long press menus, and drag and drop. 
> 
> Being able to drag scroll a web page or view with interactive controls in it is here to stay, and nets out way better than having to use a separate scroll bar, but there are still tons of fixed position controls that should act on press, and it is good UI design to favor them when possible. 
> 
> In the early days of mobile VR, the system keyboard was a dedicated little OpenGL app that responded instantly. With full internationalization it became prudent to turn it into a conventional Android app, but the default act-on-release button behavior made it feel noticeably crappier. The design team resisted a push to change it, and insisted on commissioning a user study, which is a corporate politics ploy to bury something. I was irritated at how they tried to use leading questions and tasks, but It still came back one of the clearest slam-dunks I have seen for user testing – objectively less typos, expressed preference, and interview comments about the act-on-press version feeling “crisper” and “more responsive”. 
> 
> So, I won that one, but the remaining times I brought it up for other interfaces, I did not, and you still see act-on-release throughout the Meta VR system interfaces.