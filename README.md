1.	Open wallet on your desktop.
Click Settings -> Options -> Wallet
Check "Enable coin control features"
Check "Show Masternodes Tab"
Press Ok
Restart ADVANCE Wallet and wait until it syncs to ADVANCE network. Check status by hovering the mouse pointer over the right bottom icons.
 
2.	Create a receiving address for the Masternode collateral funds.
Go to File -> Receiving addresses...
Click New, type in a label and press Ok.
 
3.	Select the row of the newly added address and click Copy to store the destination address in the clipboard.
4.	Send exactly 1000 ADVANCE to the address you just copied. Double check you've got the correct address before transferring the funds.
5.	After sending, you can verify the balance in the Transactions tab. This can take a few minutes to be confirmed by the network.
6.	Open the debug console of the wallet in order to type a few commands.
Go to Tools -> Debug console
7.	Run the following command: masternode genkey
 
You should see a long key that looks like:
3HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg
We will use this later on both cold and hot wallets.
8.	Run masternode outputs command to retrieve the transaction ID of the collateral transfer.
You should see an output that looks like this:
[
   {
     "txhash" : "6782efab3a76fa557370ec3b9c13bf0d0df3d4df63adc018e1dd90e1c8da088e",
     "outputidx" : 1
   }
]
Both txhash and outputidx will be used in the next step.
9.	Go to Tools -> Open Masternode Configuration File and add a line in the newly opened masternode.conf file. The file will contain an example that is commented out, but based on the above values, I would add this line in:
10.	MN1 45.76.33.125:30888 3HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 6782efab3a76fa557370ec3b9c13bf0d0df3d4df63adc018e1dd90e1c8da088e 1
Where 45.76.33.125 is the external IP of the masternode server that will provide services to the network.
If you want to control multiple hot wallets from this cold wallet, you will need to repeat the previous 2-10 steps. The masternode.conf file will contain an entry for each masternode that will be added to the network.
11.	Restart the wallet to pick up configuration changes.
12.	Go to Masternodes tab and check if your newly added masternode is listed under the My Masternodes tab.
At this point, we are going to configure our remote Masternode server.
