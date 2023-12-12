- The server is the one providing the graphics resources and keyboard/mouse events to applications - i.e. it runs on the computer that the human is sitting in front of
- The clients are applications which can run anywhere on the network. They receive events from the server, do whatever they need to do, and render to the user via the server API

# Direct Rendering Infrastructure
> In the classic [X Window System](https://www.wikiwand.com/en/X_Window_System "X Window System") architecture the X Server is the only process with exclusive access to the [graphics hardware](https://www.wikiwand.com/en/Video_card "Video card"), and therefore the one which does the actual [rendering](https://www.wikiwand.com/en/Rendering_(computer_graphics) "Rendering (computer graphics)") on the [framebuffer](https://www.wikiwand.com/en/Framebuffer "Framebuffer"). All that X clients do is communicate with the X Server to dispatch rendering commands. Those commands are hardware independent, meaning that the [X11 protocol](https://www.wikiwand.com/en/X_Window_System_core_protocol "X Window System core protocol") provides an [API](https://www.wikiwand.com/en/Application_programming_interface "Application programming interface") that abstracts the graphics device so the X clients don't need to know or worry about the specifics of the underlying hardware.

By 1998, OpenGL had "become the 3D API of choice in the UNIX community" [2](https://dri.sourceforge.net/doc/design_high_level.html) 



Some history: https://web.archive.org/web/20091111071410/http://www.art.net/~hopkins/Don/unix-haters/x-windows/disaster.html
Original DRI high level design doc: https://dri.sourceforge.net/doc/design_high_level.html