# Errata for *C++20 Recipes*

On **page 229 (Listing 7-10)** [code]:
 
int main(int argv, char *argc[])

should be

int main(int argc, char *argv[])

Names argc and argv are reversed.

***

On **beginning on page 231 (Listings 7-11 through 7-17)** [code]:
 
int main(int argv, char *argc[])

should be

int main(int argc, char *argv[])

Names argc and argv are reversed.

***

On page 300 [code]

In Listing 9-13, the function  void foo(T) has no implementation. The code fails to link.

***
On **pages 325 and 330** [code}

In Listings 10-13 and 10-14, the move-assignment function
    SmartPointer<T>& operator=(SmartPointer<T>&& other) is missing the
     return *this;
statement. This code will fail to compile if an attempt is made to use the move-assignment operator.

***

On **page 342** [code]

In Listing 10-18, Code as printed does not compile due to undefined variable "I" (upper-case). The line
    unsigned int squared{ i*i*I };
should be
    unsigned int squared{ i*i*i };
as it appears in the GitHub repo code, or should be
    unsigned int squared{ i*i };
to more closely match the variable name "squared."

***
On **page 370** [technical accuracy]

Contrary to the statement in the last paragraph on page 369, Figure 11-3 on page 370 does not show output from main occurring in the middle of the output from ThreadTask. Output from main occurs first.

***
On **pages 418 and 424** [technical accuracy, Listings 11-16 and 11-17]

The member function
    int operator *() const throw(int)
uses dynamic exception specification 'throw(int)' which was removed in C++17. It should not be used in C++20 code.

***
On **page 442** [incorrect link]:
 
The link on page 442 seems to be incorrect, it allows the reader to download the “ws2_32.*dll*” 
file, not “ws2_32.*lib*”, that is mentioned by the authors.

Here is another link.  The lib file is also included if you download MS Windows developers kit for their OS from Microsoft; it varies by platform.  There is a dll2lib conversion app for free available as well.

https://urldefense.proofpoint.com/v2/url?u=https-3A__osdn.net_projects_sfnet-5Fhitcrawler_downloads_lib_WS2-5F32.LIB_&d=DwIDaQ&c=vh6FgFnduejNhPPD0fl_yRaSfZy8CWbWnIf4XJhSqx8&r=po13CRlOUpXQrhiNAhMqlDkdm-GoLvfsXaFPvuim0SQ&m=3zsFEO1m-TxUy7a2FPRa_wDKY69YbZ8GM4RRYrQxJyk&s=WJQb7aNDAI3zpqUeY-eQ2WlDvnM74JBztgGjydPreS8&e=


***

In **Chapter 12** [code]:
 
In the various code listings, the Socket class does not compile when building for release.

The <sstream> header is included only if NDEBUG is not defined, but the Socket::Send function takes a stringstream object as a parameter and the Socket::Receive function returns a stringstream object. If the NDEBUG is defined the <sstream> header is not included and stringstream is an undefined type.

***

On **pages 483 and 494** [code: Listings 12-8 and 12-9]:
 
The client code (Listing 12-9) reads the answer from cin using the extraction operator >>. This stops at the first space, so will only read the word "Washington" from the input "Washington DC". The code should be changed to use getline rather than the extraction operator.

The server code (Listing 12-8) reads the received answer from the stringstream object using the extraction operator. Again, this stops at the first space character so even after the client is fixed to send "Washington DC" to the server, the server will only see the first word and report an incorrect answer. As with the client, the code should retrieve the answer from the stream with the getline function.

***
On **pages 500 and 501** [code; Listings 13-1 and 13-1b]

Both of these programs crash at their end, apparently because the sol::state destructor is called both explicitly in code and again at the end of the main function. I believe the explicit calls to the destructor should be removed.

***

On **page 582** [code}

In Listing 14-11, the program uses std::ifstream but does not #include <fstream>. Program as printed does not compile.

***

On **page 583** [code]

In Listing 14-11, the Function void GetImageData() const should return void*, not void. Additionally, Data member m_pImageData of class Texture should be of type void *, not void.

***

On **page 584** [code]

In Listing 14-11, the 2nd constructor of class Texture (taking 5 parameters), the fifth parameter (pImageData) should be of type void *, not void.

***

On **pages 561 and 599** [code]

In Listings 14-6 and 14-11, the programs use WinMain rather than main, without #including windows.h. Thus neither program compiles successfully.

***
