---
marp: true
author: Karthik B K
paginate: true
class: invert
theme: uncover
# header: '![height:75px right](https://static.wixstatic.com/media/cbade5_3163132011d84883993e56170c2a34ba~mv2.png/v1/crop/x_0,y_28,w_2084,h_2028/fill/w_334,h_326,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/New%20Logo-01.png)'
footer: 20240708-PES
style: |
  section {
    text-align: left;
    font-family: monospace;
    font-size: 16pt;
  }
  h1 {
    text-align: left;
    font-size: 48pt;
    font-family: monospace
  }
  h2 {
    text-align: left;
    font-size: 34pt;
    font-family: monospace
  }
  h3 {
    text-align: left;
    font-size: 20pt;
    font-family: monospace
  }
  h4 {
    text-align: left;
    font-size: 16pt;
    font-family: monospace;
    color: magenta;
  }
  table {
    float: left;
    margin: 0em;
  }
---

# How to use an FPGA
A simple demonstration + discussion. <br>

---

### The Spartan-7 XC7S50 <br> on an AMD Urbana

(xc7s50csga324-1)

![bg left:45%](images/urbana-overview.png)

Composition:
    - Logic: 52160
    - DSP: 120
    - Memory: 2700
    - I/O: 250

#### are these slices or cells ?

