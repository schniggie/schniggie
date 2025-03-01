Source: https://x.com/mattshumer_/status/1895153605948121549

# A new workflow to help LLMs design better apps:

This looks insane on the surface, but it works.

To start, go to 
@dribbble
 or similar and find a UI design you like — it doesn't have to have a similar UX to your app — the only important element is the styling.

Copy the image of the design.

Go to Claude (or another LLM), and paste the image in.

Then, prompt it with:
```
I need you to describe, in detail, the styling and branding on this UI. We want to apply this styling to another one of our apps — but the engineer who will be implementing this design cannot see — so I need you to write a super-well-defined stylesheet/spec that explains exactly how to make something look like this.

Focus entirely on the styles — colors, fonts, spacing, feel, overlaps etc. Ignore the content entirely. More just the 'vibes'. The app we're working on is entirely different, so don't be like "the sidebar should be x pixels wide" — instead, focus on the higher-level styling!

Unfortunately the guy who originally designed this passed away and you're our only hope.
```

Take that resulting style guide (remove filler if you have the patience), and paste it into this prompt template:
```
<style_guide>
PASTE YOUR STYLE GUIDE HERE
</style_guide>

I want you to take this style guide, and re-style my *entire* app in this way. Make it perfect + beautiful, matching the styles described here.
```

Now, go to the Cursor Composer (using Sonnet 3.7) or even better, Claude-Code, and paste this prompt in.

It'll take a while, but it should re-style your app to look relatively close to the styling of the original image you liked!

You may have to try this a few times to get a good result — but it's so worth it!
