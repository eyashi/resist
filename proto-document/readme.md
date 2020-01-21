# Prototyping the document interface

Simple text editor that does some *secret* spooky stuff in the background. Would even be interesting to use the Google Docs API as an interface at one point. Editing in a familiar interface may highten the value/*spooky* of the experience.

[Quill](https://quilljs.com/) looks to be the right bone to pick for a first draft.

The Quill.js API allows for event tracking and therefore response to changes in the document. This also has an interface for adding text back or deleting it. The "Delta" object is a document structure which can represent the contents and changes within a document, "expressing the instructions starting from an empty document." [Here is a rich explanation of the Delta concept](https://quilljs.com/guides/designing-the-delta-format/).

[Operational Transformation](https://en.wikipedia.org/wiki/Operational_transformation) is a related and interesting topic regarding the nature and structure of collaborative documents.

>The basic idea of Operational Transformation is to transform (or adjust) the parameters of an editing operation according to the effects of previously executed concurrent operations so that the transformed operation can achieve the correct effect and maintain document consistency.

The two of these elements together (Deltas and OT) may inform the way that the inference of meaning and the control structure of the documents "resistance" comes together. A removal of a particular section will emit an event that will contain the removed section (in Delta form, suppose it would be something like `{ delete: "A sentence"}` ). The Delta object can be extended to contain meta features which explains *why* that text existed in the first place, and the program can evaluate if a similar idea still belongs in the document. It can then "reverse" the decision to remove that sentence by regenerating the original purpose, and perhaps even strengthening the argument (being asked to delete something when you *know* its true should result in an argumentative response).

It is also in this instance that it can accept proposed changes. The Delta is consistent with the document's worldview, and therefore it belongs. This can remain in an unedited state, or the document can try to take in this new information and synthesize it in "its own words". Whichever ties together the document the best. Operational transformation in this respect seeks to create an abstraction for the user: their exact words are 'heard' by the system but not necessarily accepted. They are altered as needed and then installed into the document.