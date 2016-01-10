# Introduction #

This page will give detailed information on how the Amstrad Mailboard interface was designed.

# Details #

**Mailboard Pinout**

The following pin-out information is 100% credited to http://inputplus.co.uk/ralph/emailer/e2_pinouts.txt

The Mailboard is directly compatible with the PS/2 specification. The pins are arranged in the following order when looking down on the Mailboard, keys facing up.

|PIN|SIGNAL|
|:--|:-----|
|1  |GND   |
|2  |DATA  |
|3  |CLOCK |
|4  |+5V   |

**Extra information**

- When the bus is idle, clock and data lines are high.<br>
- The data line should be sampled on the rising edge of the clock pulse.<br>
- Works fine off a 3.3V supply - tested down to 2.4V.<br>
- Data bytes are transmitted as follows:<br>

<table><thead><th>BIT</th><th>DATA</th><th> </th></thead><tbody>
<tr><td>Start</td><td>-   </td><td>0</td></tr>
<tr><td>Data</td><td>s   </td><td>D0</td></tr>
<tr><td>Data</td><td>c   </td><td>D1</td></tr>
<tr><td>Data</td><td>a   </td><td>D2</td></tr>
<tr><td>Data</td><td>n   </td><td>D3</td></tr>
<tr><td>Data</td><td>c   </td><td>D4</td></tr>
<tr><td>Data</td><td>o   </td><td>D5</td></tr>
<tr><td>Data</td><td>d   </td><td>D6</td></tr>
<tr><td>Data</td><td>e   </td><td>D7</td></tr>
<tr><td>Parity</td><td>-   </td><td>(odd)</td></tr>
<tr><td>Stop</td><td>-   </td><td>1</td></tr></tbody></table>

<b>Scancodes</b>

<table><thead><th>Key</th><th>Code(hex)</th></thead><tbody>
<tr><td>store</td><td>70       </td></tr>
<tr><td>setup</td><td>7a       </td></tr>
<tr><td>services</td><td>46       </td></tr>
<tr><td>games</td><td>7c       </td></tr>
<tr><td>internet</td><td>77       </td></tr>
<tr><td>home</td><td>72       </td></tr>
<tr><td>office</td><td>69       </td></tr>
<tr><td>mobile</td><td>1a       </td></tr>
<tr><td>sms</td><td>2a       </td></tr>
<tr><td>email</td><td>1c       </td></tr>
<tr><td>fax</td><td>15       </td></tr>
<tr><td>stop</td><td>71       </td></tr>
<tr><td>1  </td><td>74<      </td></tr>
<tr><td>2  </td><td>73       </td></tr>
<tr><td>3  </td><td>6b       </td></tr>
<tr><td>4  </td><td>22       </td></tr>
<tr><td>5  </td><td>1b       </td></tr>
<tr><td>6  </td><td>1d<      </td></tr>
<tr><td>7  </td><td>1e       </td></tr>
<tr><td>8  </td><td>79       </td></tr>
<tr><td>9  </td><td>7d       </td></tr>
<tr><td>0  </td><td>75       </td></tr>
<tr><td>del</td><td>6c       </td></tr>
<tr><td>q  </td><td>21       </td></tr>
<tr><td>w  </td><td>23       </td></tr>
<tr><td>e  </td><td>24       </td></tr>
<tr><td>r  </td><td>26       </td></tr>
<tr><td>t  </td><td>52       </td></tr>
<tr><td>y  </td><td>5d       </td></tr>
<tr><td>u  </td><td>0d       </td></tr>
<tr><td>i  </td><td>0e       </td></tr>
<tr><td>o  </td><td>32       </td></tr>
<tr><td>p  </td><td>34       </td></tr>
<tr><td>enter</td><td>2c       </td></tr>
<tr><td>a  </td><td>31       </td></tr>
<tr><td>s  </td><td>33       </td></tr>
<tr><td>d  </td><td>35       </td></tr>
<tr><td>f  </td><td>36       </td></tr>
<tr><td>g  </td><td>29       </td></tr>
<tr><td>h  </td><td>5b       </td></tr>
<tr><td>j  </td><td>03       </td></tr>
<tr><td>k  </td><td>76       </td></tr>
<tr><td>l  </td><td>3a       </td></tr>
<tr><td>@  </td><td>3b       </td></tr>
<tr><td>lshift</td><td>3c       </td></tr>
<tr><td>z  </td><td>3d       </td></tr>
<tr><td>x  </td><td>4e       </td></tr>
<tr><td>c  </td><td>54       </td></tr>
<tr><td>v  </td><td>0b       </td></tr>
<tr><td>b  </td><td>05       </td></tr>
<tr><td>n  </td><td>41       </td></tr>
<tr><td>m  </td><td>42       </td></tr>
<tr><td>?  </td><td>43       </td></tr>
<tr><td>up </td><td>3e       </td></tr>
<tr><td>rshift</td><td>55       </td></tr>
<tr><td>print	</td><td>83       </td></tr>
<tr><td>address book</td><td>06       </td></tr>
<tr><td>symbol</td><td>49       </td></tr>
<tr><td>space</td><td>4b       </td></tr>
<tr><td>;  </td><td>44       </td></tr>
<tr><td>left</td><td>16       </td></tr>
<tr><td>down</td><td>2e       </td></tr>
<tr><td>right</td><td>09       </td></tr></tbody></table>

- Note that when a key is pressed, the scan code is sent as a single byte. <br>
- When the key is released it is transmitted as two bytes, first the prefix of 0xf0 followed by the scan code itself.