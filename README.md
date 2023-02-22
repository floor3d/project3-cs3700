### High-level approach
  Our approach mainly was based on solving the router problems by delegating to different methods
  thus spreading the problem out. For example, each message would go to its own handler, which
  would perhaps delegate to other methods to get specific tasks done (i.e. aggregate routes),
  etc. 
  Oftentimes much of the functionality would be as simple as looping through a forwarding table
  or creating a new object with a different src and dst to send a message copy. However, in some
  instances, more complex methods were adopted such as binary translation of IPs and netmasks.

### Challenges we faced
  It was difficult to get started with this project. Getting our bearings and figuring out the 
  starter code (as short as it was) was an important step that took longer than expected. Further,
  oftentimes we looked over small things, for example that withdraw messages held an array of networks
  and not just a single network, or that IP disaggregation may require the change of several IPs.
  On that note, IP aggregation was difficult for us to fully understand, but once we understood the
  idea behind it, it was simple to translate into code. 
  Other than that, we had difficulties with general bugs we created along the way, for example we
  misformed objects several times and messed up "src" and "dst" several times. These were mainly
  lapses of the mind and not as much lack of understanding.

### Features / Design Choices we thought were good
  Our disaggregation algorithm was generally pretty well thought out. We did not recreate the entire
  table from scratch, but rather keep track of the ip's we aggregated and were able to simply pull
  them right back once their aggregation partner was removed. It was much simpler and takes less time.
  Further, our way to compare networks and netmasks was also pretty good. By converting the network
  and netmasks into binary strings, it allowed easy comparison of networks and also facilitated 
  aggregation and disaggregation calculus which happens on a bit level.
  We tried to keep the code simple and easy to read, and not have too much code per method, so that
  it is clear to any onlookers what each function does. 

### How we tested the code
  For testing code, we employed three main strategies.
  1. Running it through the simulator. There is no better way to see if the code works than to run
  it in a simulation that checks for correctness.
  2. print checking. When we realized there was an error in our logic or the simulator was returning
  errors, we always made sure to print the events that were going on, for example which networks
  were in our forwarding table and which networks we were aggregating, to make sure that our logic
  was sound. This helped tremendously because it identified exactly where we went wrong so we could
  check over the code that was causing errors.
  3. Logic checking in environment. For more technical functionalities like transforming a netmask
  into a binary representation, we ran the code by itself in a python3 environment with dummy data
  to make sure that the function did its job correctly and did not run into any runtime errors. 
  This helped to get our functionality working even before we simulated it.
