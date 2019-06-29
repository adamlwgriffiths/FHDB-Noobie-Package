HDLoader Game Manager Client for HDLGameInstaller v0.821	- 2018/12/08
----------------------------------------------------------------------------

This is the PC-side network client for the HDLGameInstaller v0.815 and above.

Notes on network support:
--------------------------------
*Please ensure that TCP port 45061 & 45062 are allowed in your network.

Changelog:
----------
2018/12/08:
	*Increased data connection timeout to 80s, to allow the server's connection attempts to be exhausted before the PC client indicates an error.
	*Added a prompt to delete the game if it was already installed, when the user adds a game to install.

2018/11/24:
	*Attempted to fix the problem with compatibility settings not binding at installation time.
	*Added timeout for the data connection, to prevent the software from getting stuck if the connection gets blocked.

2018/11/18:
	*Attempted to make the data connection close gracefully regardless of the OS used, with all data successfully sent and received by the other end.

2018/10/28:
	*Fixed order of controls for game update form.
	*Success message will no longer be displayed if the user aborts a game installation.

2018/06/04:
	*Changed I/O strategy to match the PlayStation 2 side: 32x512KB ring buffer.
	*Adjusted control sizes and placement on install dialog box. DVD is now the default disc type.
	*Adjusted network protocol for quicker transfer of game list.
	*Removed old TCP_NODELAY setting for better utilization of the command socket.
	*Fixed division by zero glitch during installation and game copying.

2018/05/29:
	*Corrected incorrect logic that lead to an installation continuing, even if the user has cancelled the installation.

2018/05/27:
	*Revamped protocol to have as little overhead during file transfer, as possible.
	 Opens port 45062, which is dedicated for data transfer.
	*Added more reconnection code to improve robustness of data transfer.

2018/05/23:
	*Added free disk space indicator.
	*Fixed order of controls (pressing tab should now correctly select the next control).
	*Added a current speed indicator, which indicates the speed at which the last block was transferred at.
	*Increased block size, for improved transfer performance (256KB x 4 -> 4MB x 4).
	*Fixed progress bar not being updated correctly.
	*Added I/O manager to allow data to be read/written in the background.

2017/02/25:
	*Removed support for compressed transfers.
	*Improved reading method for MODE 1/2048 ISO9660 disc images.

2017/02/19:
	*Reduced memory usage.

2017/02/18:
	*Game list will no longer be fully refreshed after a game is edited or deleted.

2017/02/11:
	*Adjusted to allow data to be read and compressed first, before the actual read request takes place.

2017/02/04:
	*Fixed and improved support for automatic reconnection.
	*Added support for compressed transfers.
	*Games can now be queued for installation.
	*Installed games can now be copied back onto the PC.

2015/06/25:
	*Added support for reconnecting.
	*Added a timeout for receiving on the client side.

Credits:
	This software may have been worked on mainly by me,
	but I had the support of other users:
		All closed-beta testers!
	Special thanks to tinostar91, grahf & Jolek for helping with the testing and improvements to network support.
