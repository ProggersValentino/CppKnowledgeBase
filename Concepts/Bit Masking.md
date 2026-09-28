ref: [Bit Masking - CPPLearn](https://www.learncpp.com/cpp-tutorial/bit-manipulation-with-bitwise-operators-and-bit-masks/), [Bitwise Operations](https://www.learncpp.com/cpp-tutorial/bitwise-operators/) 

Bit masking is a technique used to efficiently modify individual bits. This is done through creating a set of masks that represent each individual bit and then using that bit to turn on and off that specific bit position

``` c++
constexpr std::uint8_t mask0{ 1 << 0 }; // 0000 0001
constexpr std::uint8_t mask1{ 1 << 1 }; // 0000 0010
constexpr std::uint8_t mask2{ 1 << 2 }; // 0000 0100
constexpr std::uint8_t mask3{ 1 << 3 }; // 0000 1000
constexpr std::uint8_t mask4{ 1 << 4 }; // 0001 0000
constexpr std::uint8_t mask5{ 1 << 5 }; // 0010 0000
constexpr std::uint8_t mask6{ 1 << 6 }; // 0100 0000
constexpr std::uint8_t mask7{ 1 << 7 }; // 1000 0000
```

As shown above, the set of masks allow us to precisely change a single bit within the range of an 8 bits, if we want to have that same precision for 32-bits then we would need a set of 32 bit masks

``` c++
	std::uint8_t flags{ 0b0000'0101 }; // 8 bits in size means room for 8 flags

	std::cout << "bit 0 is " << (static_cast<bool>(flags & mask0) ? "on\n" : "off\n");
	std::cout << "bit 1 is " << (static_cast<bool>(flags & mask1) ? "on\n" : "off\n");
```


### Extracting Specific set of bits
We can also use masking as a filter to extract and isolate a certain number of desired bits. this method is very useful for when you only want to copy over a specific amount of bits. A real world example is [Bit packing](https://gafferongames.com/post/reading_and_writing_packets/)  

take the 32-bit binary: `0000'0000 0000'0000 0000'0011 1110'1000 ```
which in decimal is: 1000

but however we only need the **first 6 bits** of the binary. While we could just loop through each bit and copy it over 6 times to achieve this affect, it is very slow and unnecessary given the bitwise tools we have to manipulate bits. 

So then instead we create a mask where we establish we only want the first 6 bits which looks like:
``` c++
int mask = (1 << 6)
//binary output: 0000'0000 0000'0000 0000'0000 0100'0000
```

this is close but theres still one more step, as you see above when we do `(1 << 6)` we are turning on the 6th (7th if counting from 1) bit when we count from 0 which is equal to a value of **64**

so obviously this is not what we want so we need to do the extra step of **minus 1** from the value which will look like:
``` c++ 
int mask = (1 << 6) - 1
//binary output: 0000'0000 0000'0000 0000'0000 0011'1111
```

So now, counting from 1, we have a mask with the **first 6 bits activated** which the **value is 63**
Therefore, for this method to work you just need to distinguish that counting from 1 how many bits you want **minus 1**

Now, going back to our problem where want to extract the first 6 bits in our 32-bit binary number with our knowledge of bitwise operations we can do something like this:
``` c++ 
uint32_t number = 1000;
//binary representation: 0000'0000 0000'0000 0000'0011 1110'1000

int mask = (1 << 6) - 1;
//decimal representation: 63
//binary representation: 0000'0000 0000'0000 0000'0000 0011'1111

uint32_t buffer |= mask & number; 
//binary output: 0000'0000 0000'0000 0000'0000 0010'1000


```