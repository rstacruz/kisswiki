- language
  - https://swift.org/blog/swift-api-transformation/
  - https://developer.apple.com/swift/blog/?id=29
  - http://www.infoworld.com/article/3027100/mobile-development/seven-swift-2-enhancements-every-ios-developer-will-love.html
  - roadmap https://github.com/apple/swift-evolution/blob/master/README.md
- game
  - https://medium.com/magnetis-backstage/your-first-ios-game-fda99504c3e4
  - http://open.bekk.no/a-swift-run-through-making-an-ios-game
- job
  - http://artsy.github.io/blog/2016/01/30/iOS-Junior-Interviews/
  - https://www.natashatherobot.com/swift-jobs/
  - http://www.indeed.co.uk/Swift-Developer-jobs
  - https://www.freelancer.com/jobs/iPhone/1/
  - https://www.upwork.com/o/jobs/browse/?q=swift
- vs
  - http://www.slideshare.net/KyleSherman/swift-at-linkedin
  - objective-c
    - http://ericasadun.com/2016/02/08/when-your-client-demands-swift/
    - For larger apps, well, I have a Swift app that isn't really very big, probably still small but significantly bigger than a tutorial, and it keeps freezing Xcode. (Edit something in Interface Builder, switch to the ViewController class with IBOutlets in it, then switch back and forth between ViewControllers making edits. Each time it takes longer and longer until I just force-quit Xcode to avoid twiddling my thumbs for 5 minutes.) So I don't think Swift is ready for any app that isn't pretty small anyway. https://news.ycombinator.com/item?id=10925916
    - I think the gain is mostly that Swift allows you write code which more resistant to bugs than its ObjC counterpart would be. In Yaron Minsky's "Effective ML" talk, he mentions the idea of "Make illegal states unrepresentable": https://vimeo.com/14313378 The combination of enums and non-optional variables allows you to get much closer to this ideal than you could with ObjC. https://news.ycombinator.com/item?id=10925793
    - Yeah as nice as Swift is, Cocoa was designed for Objective-C.  
      e.g. -[NSBezierPath setLineDash:count:phase:] takes a C array in Objective-C, but an UnsafePointer<CGFloat> in Swift.  
      Apple needs new API interfaces for their new language, and that will take time.  
      https://news.ycombinator.com/item?id=10925668  
      This will improve in Swift 3.0, via an improved mapping of Cocoa APIs into Swift (naming wise):  
      https://github.com/apple/swift-evolution/blob/master/proposals/0005-objective-c-name-translation.md  
      At some point in the future I imagine we would also see native Swift APIs.  
      https://news.ycombinator.com/item?id=10927557
    - We tried using Swift for a new app but the language isn't ready for prime time. It's an impressive language by itself, but the support for it just isn't there yet. Since it's still in infancy things change too much and documentation/stackoverflow is pretty weak. Our app was simple but we spent more time trying to make it work than actually programming and ended up doing an obj-c rewrite in less time. I'm sure this scenario won't be the case for long, but it's the case for now. https://news.ycombinator.com/item?id=10924737
    - So far there are some performance issues with containers as value types. Other bottlenecks are structs that contain many references types. https://news.ycombinator.com/item?id=10924984
    - http://www.slideshare.net/KyleSherman/swift-at-linkedin/31
    - Cocoa is vastly easier to use since APIs return the correct types (instead of the ambiguous Objective-C "AnyObject") and error handling is now easy (instead of pure torture) https://www.reddit.com/r/swift/comments/3cre4i/seven_months_ago_someone_asked_if_it_was_viable/csyb6ow
    - Once the language is stable and established, Apple may well decide it doesn’t want to support two languages and will start requiring developers to use Swift for certain aspects of coding. This probably won’t happen for years, but Wenderlich say he expects it to happen at some point. “Then people will start to migrate to Swift,” he says, "and eventually Objective C will go away.”  http://www.bloomberg.com/news/articles/2015-06-04/apple-s-big-breakthrough-that-almost-no-one-knows-about-swift-code
    - https://www.reddit.com/r/iOSProgramming/comments/46jzx1/swift_vs_objectivec/
    - [Swift] still needs to add it's own runtime in the binary https://www.reddit.com/r/iOSProgramming/comments/46jzx1/swift_vs_objectivec/d05qwic, its runtime libraries are bundled with iOS instead of with each app separately https://www.reddit.com/r/iOSProgramming/comments/46jzx1/swift_vs_objectivec/d05t9la
    - Objective‑C of a Hello World app is 72k vs. Swift, 3.1mb; full version: Objective‑C, 92k vs. 4.6mb. https://realm.io/news/ben-sandofsky-time-for-swift/
- most loved - swift http://stackoverflow.com/research/developer-survey-2015#tech-super
- learn
  - http://blog.pusher.com/5-reasons-you-should-learn-swift-in-2016-2/
  - https://www.hackingwithswift.com/test/
  - https://www.reddit.com/r/swift/comments/469559/what_sources_can_you_recommend_where_an_absolute/
  - http://www.ios-blog.co.uk/tutorials/all/
  - https://developer.apple.com/library/ios/referencelibrary/GettingStarted/DevelopiOSAppsSwift/
  - https://github.com/allenwong/30DaysofSwift
  - https://www.hackingwithswift.com/example-code/
  - https://littlebitesofcocoa.com/
- 89% of top 100 apps don't use Swfit (2016-01-10) https://medium.com/art-marketing/are-the-top-apps-using-swift-42e880e7727f
- style guide https://github.com/SlideShareInc/swift-style-guide/
- migrattion
  - tips from Objective-C https://www.reddit.com/r/swift/comments/451xmo/transitioning_from_objective_c_to_swift_without/
  - example http://blog.tarkalabs.com/2016/02/16/refactoring-swift/
  - remember to mark methods as @dynamic if you're passing a selector to them, or you (may or may not) get a nasty crash when the selector is called https://www.reddit.com/r/iOSProgramming/comments/46jzx1/swift_vs_objectivec/d05sx2o
- https://github.com/vsouza/awesome-ios#getting-started
- https://www.reddit.com/r/swift/comments/456y2c/what_are_some_of_the_best_swift_app_github_repo/
- news
  - http://nshipster.com/
- server https://github.com/crossroadlabs/Express
- https://github.com/realm/realm-cocoa
- http://www.swiftgl.org/

## Foundation and runtime

Runtime - to biblioteka do komunikacji binarki ze środowiskiem. Jest dla obj-c czy dla swift https://en.wikipedia.org/wiki/Runtime_library

Runtime dla swift ma być ustabilizowany w 3.0 https://github.com/apple/swift/blob/master/docs/Runtime.md

i wtedy dopiero będzie system-wide i nie trzeba będzie dołączać runtime do binarek

ale to nie znaczy że swift jest kompilowany just-in-time czy coś innego

A tutaj jacyś goście robią własną implementację Foundation https://github.com/PureSwift/SwiftFoundation

A tu Foundation od Apple https://github.com/apple/swift-corelibs-foundation
https://github.com/apple/swift-corelibs-foundation/blob/master/Docs/Status.md
https://github.com/apple/swift-corelibs-foundation/blob/master/Docs/Design.md

## Arc vs other GC

https://lists.swift.org/pipermail/swift-evolution/Week-of-Mon-20160208/009422.html
