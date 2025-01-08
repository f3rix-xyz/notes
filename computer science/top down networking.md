
- End systems connect through communication links and packet switches, with links made of physical media (coax, copper, fiber, radio) transmitting at different rates measured in bits/second
- When sending data, end system segments data and adds headers to create packets that are forwarded through network to destination for reassembly
- Packet switches (routers and link-layer switches) forward packets on communication links toward destinations, following routes/paths through network
- Access to Internet provided by Internet Service Providers (ISPs) of different tiers - residential, corporate, university ISPs connect to higher-tier ISPs creating hierarchical structure
- Network runs on protocols (rules) like TCP/IP that control information flow - IP specifies packet formats, TCP handles end-to-end communication

---

`note the below para is not imp just look at it once`

* Access networks physically connect end systems to first router (edge router)

* DSL (Digital Subscriber Line):
- Uses telephone lines
- Provides downstream (50 kHz-1MHz) and upstream (4-50 kHz) channels
- Maximum rates: 12-24 Mbps downstream, 1.8-2.5 Mbps upstream
- Distance limited to 5-10 miles from central office
- Uses DSLAM at central office to separate data and phone signals

* Cable Internet:
- Uses cable TV infrastructure (hybrid fiber-coax)
- Shared broadcast medium
- DOCSIS 2.0 allows up to 42.8 Mbps downstream, 30.7 Mbps upstream
- Uses cable modems and CMTS (Cable Modem Termination System)

* FTTH (Fiber to the Home):
- Direct optical fiber to homes
- Uses PON (Passive Optical Network) or AON (Active Optical Network)
- Can provide gigabit speeds
- Components: ONT (Optical Network Terminator), splitter, OLT (Optical Line Terminator)

* Enterprise/Home Networks:
- Ethernet most common (100 Mbps to 10 Gbps)
- WiFi (IEEE 802.11) provides wireless access up to 54 Mbps
- Home networks often combine broadband access with wireless LAN

* Wide-Area Wireless:
- 3G provides >1 Mbps
- 4G LTE offers >10 Mbps potential speeds
- Coverage range of several kilometers from base station
---

* Physical Media Types:
  * Guided Media (waves guided along solid medium):
    - Twisted-Pair Copper Wire:
      - Most common and inexpensive
      - Two insulated copper wires twisted to reduce interference
      - UTP used in LANs with rates 10 Mbps to 10 Gbps
      - Used in telephone networks and DSL
    
    - Coaxial Cable:
      - Two concentric copper conductors
      - Higher data rates than twisted pair
      - Used in cable TV and internet systems
      - Can be used as shared medium
    
    - Fiber Optics:
      - Conducts light pulses
      - Very high data rates (tens/hundreds of Gbps)
      - Low interference and attenuation
      - Used in long-distance networks and backbones
      - OC standards from 51.8 Mbps to 39.8 Gbps

  * Unguided Media (waves propagate through atmosphere/space):
    - Terrestrial Radio:
      - No physical wires needed
      - Affected by environment (path loss, fading, interference)
      - Categories: short-distance, local area, wide area
    
    - Satellite:
      - Geostationary (36,000 km orbit)
        - Fixed position
        - 280ms delay
        - Hundreds of Mbps speeds
      - LEO (Low Earth Orbit)
        - Rotate around earth
        - Multiple satellites for coverage
        - Used for future internet access


---

- Packet Switching Core Concepts:
- Store-and-forward transmission (key packet switching principle):
    - Router must receive entire packet before it can begin forwarding to next hop
    - If packet length is L bits and link rate is R bits/sec, time to transmit = L/R seconds
    - For N links end-to-end, total delay = N * L/R seconds because packet must be fully received at each hop
    - Example: For 3 packets sent over 2 links at rate R:
        - At time L/R: First packet at router, second packet transmission begins
        - At time 2L/R: First packet at destination, second at router, third transmission begins
        - At time 4L/R: All packets received at destination
- Queuing and Buffer Management:
    - Each router has output buffers/queues for each link
    - When packets arrive faster than link can transmit:
        - Packets wait in buffer creating variable queuing delays
        - Delay depends on congestion level in network
        - If buffer fills completely, new packets or buffered packets must be dropped (packet loss)
- Circuit Switching Fundamentals:
    - Resource Reservation:
        - Network reserves dedicated capacity along entire path before communication begins
        - Like restaurant reservation - guaranteed table but requires advance booking
        - Creates fixed circuit with guaranteed bandwidth for entire session duration
    - Multiplexing Methods:
        - Frequency-Division Multiplexing (FDM):
            - Divides link's frequency spectrum into bands
            - Each connection gets dedicated frequency band
            - Like radio stations each using different frequencies
        - Time-Division Multiplexing (TDM):
            - Divides time into fixed-length frames
            - Frames subdivided into slots
            - Connection gets same slot in every frame
            - Transmission rate = (frame rate × bits per slot)
- Comparison Analysis:
    - Efficiency Example:
        - Consider 1 Mbps link with users active 10% of time at 100 kbps:
        - Circuit switching: Supports only 10 users (each needs dedicated 100 kbps)
        - Packet switching: Can support 35 users because probability of >10 active users is very small (0.0004)
        - Shows how packet switching better utilizes available capacity for bursty traffic
    - Modern Trend:
        - Networks moving toward packet switching even for traditional circuit-switched services
        - Packet switching increasingly used for voice calls, especially international routes
        - Better suits modern traffic patterns and provides more efficient resource utilizatio


---
- Evolution of Internet's Network Structure:
- Structure 1 - Single Global ISP:
    - All access ISPs connect to one global transit ISP
    - Unrealistic due to cost and monopoly concerns
    - Introduces customer-provider relationship where access ISPs pay global ISP
- Structure 2 - Multiple Global ISPs:
    - Multiple competing global transit ISPs emerge
    - Access ISPs have choice of providers
    - Global ISPs must interconnect to ensure complete connectivity
    - Forms two-tier hierarchy (global ISPs at top, access ISPs at bottom)
- Structure 3 - Hierarchical Structure:
    - Introduces regional ISPs between access and tier-1 ISPs
    - Creates multi-tier hierarchy:
        - Tier-1 ISPs (~12 companies like AT&T, Sprint) at top
        - Regional ISPs in middle
        - Access ISPs at bottom
    - Each level pays the level above (customer-provider relationship)
    - Some regions have additional tiers (e.g., China's city → provincial → national → tier-1)
- Structure 4 - Additional Components:
    - Points of Presence (PoPs):
        - Router groups where customer ISPs connect to provider networks
        - Present at all levels except access ISP level
    - Multi-homing:
        - ISPs connect to multiple provider ISPs
        - Provides redundancy and failure protection
    - Peering:
        - Direct connection between same-level ISPs
        - Usually settlement-free (no payment)
        - Reduces costs by avoiding upstream providers
    - Internet Exchange Points (IXPs):
        - Physical locations where multiple ISPs can peer
        - About 300 IXPs exist globally
        - Facilitates efficient interconnection
- Structure 5 - Content Provider Networks:
    - Large providers (like Google) build private global networks
    - Connect directly to lower-tier ISPs where possible
    - Bypass higher tiers to reduce costs
    - Maintain better control over service delivery
    - Still connect to tier-1 ISPs for complete reach


* Types of Network Delay:

* Nodal Processing Delay:
  - Time router takes to examine packet header and determine routing path
  - Includes error checking of packet bits
  - Typically microseconds or less in modern routers
  - Affects router's maximum packet forwarding rate

* Queuing Delay (Most Complex):
  - Time packet spends waiting in buffer for transmission
  - Varies based on:
    - Network congestion level
    - Previous packets in queue
    - Traffic intensity (La/R - arrival rate × packet size/link bandwidth)
  - When traffic intensity approaches 1:
    - Queue length grows rapidly
    - Delays increase exponentially
    - Similar to highway traffic congestion
  - With finite queues, leads to packet loss when buffer fills

* Transmission Delay:
  - Time to push all packet bits onto the link
  - Calculated as: L/R (packet length/link bandwidth)
  - Example: 1000 bit packet on 1 Mbps link = 1 millisecond
  - Independent of distance between routers

* Propagation Delay:
  - Time for bit to travel physically from one router to next
  - Calculated as: distance/propagation speed
  - Speed typically 2-3 × 10^8 meters/second (near light speed)
  - Independent of packet size or link bandwidth

* Key Understanding:
  - Total delay = Processing + Queuing + Transmission + Propagation
  - Transmission vs Propagation analogy:
    - Transmission: Time to put cars through tollbooth (packet size dependent)
    - Propagation: Time cars take to drive between tollbooths (distance dependent)

* Queuing Loss:
  - Occurs when queue buffer fills up
  - Router must drop (lose) additional arriving packets
  - Probability of loss increases with traffic intensity
  - Lost packets may need end-to-end retransmission

This explanation maintains the depth of technical concepts while organizing them in a clear, hierarchical structure, emphasizing the relationships between different types of delay and their practical implications.

---

<div style="padding: 20px; font-family: Arial, sans-serif;">
    <div style="background: #f0f4f8; padding: 20px; border-radius: 8px; margin-bottom: 20px;">
        <h2 style="color: #2c5282;">The Journey of Digital Data</h2>
        
        <!-- First Scenario -->
        <div style="margin: 20px 0;">
            <div style="display: flex; align-items: center; justify-content: space-between;">
                <div style="background: #4299e1; padding: 15px; border-radius: 8px; color: white;">
                    Server<br>(2 Mbps)
                </div>
                <div style="height: 20px; width: 150px; background: linear-gradient(to right, #4299e1, #63b3ed); position: relative;">
                    <div style="position: absolute; top: -20px; width: 100%; text-align: center; font-size: 12px;">
                        Link 1
                    </div>
                </div>
                <div style="background: #718096; padding: 15px; border-radius: 8px; color: white;">
                    Router
                </div>
                <div style="height: 20px; width: 150px; background: linear-gradient(to right, #63b3ed, #90cdf4); position: relative;">
                    <div style="position: absolute; top: -20px; width: 100%; text-align: center; font-size: 12px;">
                        Link 2<br>(1 Mbps)
                    </div>
                </div>
                <div style="background: #48bb78; padding: 15px; border-radius: 8px; color: white;">
                    Client
                </div>
            </div>
        </div>

        <!-- Second Scenario -->
        <div style="margin: 40px 0;">
            <h3 style="color: #2c5282;">The Shared Highway</h3>
            <div style="display: flex; flex-direction: column; gap: 10px;">
                <!-- Flow 1 -->
                <div style="display: flex; align-items: center; justify-content: space-between;">
                    <div style="background: #4299e1; padding: 10px; border-radius: 4px; color: white;">S1</div>
                    <div style="height: 10px; width: 100px; background: #63b3ed;"></div>
                    <div style="height: 30px; width: 200px; background: #fc8181; position: relative;">
                        <div style="position: absolute; top: -20px; width: 100%; text-align: center; font-size: 12px;">
                            Shared 5 Mbps
                        </div>
                    </div>
                    <div style="height: 10px; width: 100px; background: #90cdf4;"></div>
                    <div style="background: #48bb78; padding: 10px; border-radius: 4px; color: white;">C1</div>
                </div>
                <!-- Flow 2 (similar structure repeated) -->
                <div style="display: flex; align-items: center; justify-content: space-between;">
                    <div style="background: #4299e1; padding: 10px; border-radius: 4px; color: white;">S2</div>
                    <div style="height: 10px; width: 100px; background: #63b3ed;"></div>
                    <div style="height: 30px; width: 200px; background: #fc8181;"></div>
                    <div style="height: 10px; width: 100px; background: #90cdf4;"></div>
                    <div style="background: #48bb78; padding: 10px; border-radius: 4px; color: white;">C2</div>
                </div>
            </div>
        </div>
    </div>
</div>


Chapter 1: The Single Path Journey

Imagine you're the only person downloading a movie. Your connection to the internet is like having two connected pipes of different sizes. The server can pump data at 2 Mbps (like a wide pipe), but your home internet connection can only handle 1 Mbps (like a narrower pipe). Just like water can only flow as fast as the narrowest pipe allows, your download speed will be limited to 1 Mbps, no matter how fast the server can send the data.

For example, if you're downloading a 100 MB movie:

- Even though the server could send it in about 50 seconds (at 2 Mbps)
- Your narrower "pipe" means it'll take about 100 seconds (at 1 Mbps)

Chapter 2: The Rush Hour Challenge

Now imagine it's evening, and everyone in your neighborhood is streaming their favorite shows. This is like having many houses drawing water from the same main pipe. Let's say there's a shared internet connection (like a main water pipe) that can handle 5 Mbps total, but ten people are trying to download simultaneously.

Even though each person has a connection that could handle 2 Mbps:

- The shared 5 Mbps link must be divided among everyone
- Each person ends up getting only 500 Kbps
- That same 100 MB movie now takes about 200 seconds to download

It's just like when everyone in the neighborhood takes a shower in the morning - the water pressure drops because everyone's using the same main pipe.

Chapter 3: The Late Night Freedom

But here's where it gets interesting. Try downloading that same movie at 3 AM when everyone else is sleeping. Suddenly, you might get your full 1 Mbps speed again because you're the only one using the shared connection. The main pipe (5 Mbps) is no longer the bottleneck because you're the only one drawing from it.

This is why internet speeds often feel faster late at night or early in the morning - just like water pressure is better during off-peak hours.

The Moral of the Story

Just as a chain is only as strong as its weakest link, your download speed is only as fast as the slowest part of the path between you and the server. It could be:

- Your own internet connection
- The server's connection
- Or any shared links in between

And just like a city's water system needs to balance the needs of all its residents, the internet must balance the needs of all its users. That's why understanding throughput helps us design better networks and set realistic expectations for our download speeds.

---


