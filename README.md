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
  h5 {
    text-align: left;
    font-size: 6pt;
    font-family: monospace;
  }
  table {
    float: left;
    margin: 0em;
  }
---

# How to use an FPGA
A simple demonstration + discussion. <br>

---

# What is an FPGA ?

---

![bg fit](images/cpu-vs-fpga.png)

<!-- source: Andi's blog about 6.2050 at MIT - https://mitadmissions.org/blogs/entry/6-2050-field-programmable-gate-awesomeness/ -->

---

# Toys for today
all the equipment that we're going to use.

---

- The AMD Urbana
- Xilinx Vivado

![bg left:55%](images/urbana.png)


---

# What FPGA does the AMD Urbana have?

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

---

# Let's play with the GPIO
#### Point them out on the board

---

### 1. Create a pointer to the base address of the LED IP
```C
#define XPAR_LED_IP_0_BASEADDR 0x0; // is this right ?
uint32_t* my_led_ptr = (uint32_t*) XPAR_LED_IP_0_BASEADDR;
```

### 2. Write a value to that address
```C
*(my_led_ptr) = 0x55;
```

#### What happened on the board ?

---

### Let's try this one more time.
This time, use the following piece of code:

```C
#include "xparameters.h"
#include "sleep.h"


uint32_t* my_led_ptr;

int main()
{
  my_led_ptr =(uint32_t*) XPAR_LED_IP_0_BASEADDR;

  while (1)
  {
    *(my_led_ptr) = 0x55;
    sleep(1);
    *(my_led_ptr) = 0xAA;
    sleep(1);
  }

  return 0;
}
```

#### What happened now ?