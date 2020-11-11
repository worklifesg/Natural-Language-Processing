### Basics of NLP

In this section of NLP, we will cover Text Cleaning and Text Processing that occurs generally in the intial steps of NLP pipeline after Data Acquisition. The fundamental understanding code (using Jupyter) and their outputs are presented below

#### 1. Strings
Here will start with general operations on text (strings)
  * Creating a string
    ```javascript
    string = 'PYTHON'
    s,type(s)
    ```
    ```
    ('PYTHON', str)
    ```
  * Depicting string index
    ```javascript
    for index, character in enumerate(s):
      print('Character ->', character, 'has index->', index)
    ```
    ```
    Character -> P has index-> 0
    Character -> Y has index-> 1
    Character -> T has index-> 2
    Character -> H has index-> 3
    Character -> O has index-> 4
    Character -> N has index-> 5
    ```
  * Printing different attributes of string
    ```javascript
    print(s[0], s[1], s[2], s[3], s[4], s[5]) #each string index
    print(s[-1], s[-2], s[-3], s[-4], s[-5], s[-6]) #string index backward
    print(s[:]) #another way to print string
    print(s[1:4])
    print(s[-3:-1])
    print(s[-3:])
    print(s[:3] + s[3:]) # Adding two strings together
    print(s[::1])  # no offset
    print(s[::2])  # print every 2nd character in string
    ```
    ```
    P Y T H O N
    N O H T Y P
    PYTHON
    YTH
    HO
    HON
    PYTHON
    PYTHON
    PTO
    ```
    
  * String Splitting & Joining
    ```javascript
    string='Hurray !,Charlie Chaplin,has written,directed and acted in his own films.'

    print(string)
    print(string.split(','))
    print(string.split('!'))
    print(''.join(s.split('!')))
    ```
    ```
    Hurray !,Charlie Chaplin,has written,directed and acted in his own films.
    ['Hurray !', 'Charlie Chaplin', 'has written', 'directed and acted in his own films.']
    ['Hurray ', ',Charlie Chaplin,has written,directed and acted in his own films.']
    Hurray ,Charlie Chaplin,has written,directed and acted in his own films.
    ```
