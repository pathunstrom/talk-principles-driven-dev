Living our Principles
===============================

1. So how are we living our principles?
2. I think principles are things that are great to believe in, but only
   matter when you apply them.
3. This is basically a demonstration of how these things affect our code.

Examples
-------------------------------

1. The `ppb` Hello World application is two lines:
   ```python
   import ppb

   ppb.run(title="hello world")
   ```
    1. As the first two lines of code a ppb user writes, we've spent some time
       improving this.
    2. Previous incarnations of ppb were longer:
       ```python
       import ppb

       with ppb.GameEngine() as ge:
           ge.run()
       ```
    3. We've slowly identified complexity in the first hour of a users time, and
       hidden it through the use of helper functions and sensible defaults.
    4. Additionally, these changes took being unafraid to throw away code.
        1. ppbv0.2.0 was an awful interface I threw out entirely for v0.3.0

2. Minimal viable game
   ```python
   import ppb

   class Player(ppb.Sprite):
       direction = ppb.Vector(0, 0)
       speed = 4
       def on_mouse_motion(self, event, signal):
           self.direction = self.position - event.position
       def on_update(self, event, signal):
           self.position += self.direction.scale_to(self.speed) * event.time_delta
   
   def setup(scene):
       scene.add(Player())
   
   ppb.run(setup)
   ```
    1. To get here from hello world requires learning a few things:
        1. functions
        2. classes
        3. The idea of events
    2. Honestly, we're not happy with this.
        1. It's missing some defaults.
        2. It's kind of tiring to write this same code over and over again
    3. Future Feature: Default sprites.
        1. They'd have various pre-supported features.
            1. Object following
            2. Move to target
            3. Mouse movement
            4. Keyboard movement
        2. This would reduce our minimum functioning game to four lines.
    4. We want this minimal example to setup a playground for end users to
       combine some basic tools to build prototypes.
    5. The goal is to provide a ramp for beginning from the first example to
       this one by only adding one new concept per step, and providing instant
       feedback.

3. Project Governance
    1. I did not set out on ppb to be a BDFL.
        1. The github organization has had an Oversight team since day one.
            1. (It's still just me)
        2. Even before the github organization
            1. Teachers had input on the API design
            2. As a hobbyist game developer, I felt their needs were covered.
            3. Students were (and are) the hardest to get feedback from.
    2. Recently, we had our first advertised strategy meeting
        1. In attendance
            1. 2 educators
            2. 1 grad student (volunteering to help with grant writing)
            3. 2 core developers
            4. A hobbyist game dev
        2. I want these meetings to continue to have a diverse membership
            1. At least half should be educators
        3. Results
            1. Short term feature set
                1. Text rendering
                2. Previously mentioned default sprites
                3. Some performance enhancements
            2. Documentation is now my highest priority as a maintainer
                1. Tutorials
                2. Detailed cook book
                3. Improved API documentation
            3. Strategic projects
                1. A strategic project is a non-core project that advances
                   the goals of the project.
                    1. Feet Python runner
                    2. Adding ppb to the Briefcase cookiecutter
                2. Distribution
                    1. Working with other distribution projects as previously
                       mentioned
                    2. ppb on the web
                        1. We've identified an path to getting ppb games to run
                           in the browser.
                        2. Will be in the pipeline in the next six months.
