AMP has a number of different release streams that are available at any given time. Generally speaking users should stay with the Mainline release stream unless they have a particular reason to use a different one.

Mainline
---
These builds are the main releases that get shipped to all users by default, and are announced on the Forums/Discord/Twitter etc. They have both a version number and a codename (the same codename is used for multiple releases within a given feature set). These releases are tested before release and what most users should be using at any given time.

FastTrack
---
FastTrack builds are produced weekly, they only receive automated testing. Generally these are reasonably stable but are subject to some of the issues of Nightly builds.

Nightly
---
These builds are produced every day at around 4AM GMT. They include all of the previous days changes. These builds go through only basic unit tests and minimal integration testing. They will often include work-in-progress or partial changes, so may occasionally have non-functioning new features or partial bug fixes. They're also liable to straight up break entirely. It is strongly recommended not to have anything update to these automatically and to only use them if you need a specific very new feature/fix or want to test out new stuff on a non-critical system.

Bleeding
---
Also known as Continual Integration (CI) builds, these builds are up-to-the second output produced whenever a change is made to AMP at all. Using these builds requires that you own either a Patreon Supporter, Network Premium, Enterprise, Black or Platinum edition licence. As with nightly these are risky builds to use.