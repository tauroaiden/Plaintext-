def text_clean( text, LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#'):
    """
    Arguments:
        text (str): a piece of text for cleaning
        LETTERS (str, optional): defines the alphabet of allowable characters
    Returns:
        (str): text with only the characters also found in LETTERS
               lower-case letters in text will be made upper-case  
    """
    cleaned_text = '' 
    
    for character in text: 
        if character.upper() in LETTERS:
            cleaned_text += character.upper()
    
    return cleaned_text
    
    def binary_convert(text, LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#"):
    text = text_clean(text).replace(' ','')
    message = ''
    for char in text:
        message += binary[char]
        
    return message
    
    def roman_convert(text, LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#"):
    message = text.replace(' ','')
    output = ''
    count = 0
    for i in range(int(len(message)/5)):
        p = message[count:count+5]
        output += roman_char[p]
        count = count + 5
    output = output.lower()
    return output
    
    def xor_function(messagestring, keystring):
    yum = int(len(messagestring)/len(keystring))
    bum = len(messagestring)%len(keystring)
    nkeystring = ''
    for i in range(yum):
        nkeystring += keystring
    nkeystring += keystring[0:bum]
    message = int(messagestring,2) ^ int(nkeystring,2)
    message = '{0:b}'.format(message)
    dif = len(messagestring) - len(message)
    ping = ''
    if (dif>0):
        for i in range(dif):
            ping += '0'
    return ping + message
    
    def xor_encrypt(message, key, encrypt = True, LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#"):
    binm = binary_convert(message)
    xord = xor_function(binm, key)
    return roman_convert(xord).upper()
    
    def caesar(message, key, LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#"):
    message = text_clean(message)
    output = ""

    for char in message:
      index = LETTERS.find(char)
      newindex = (index + key) % len(LETTERS)
      output = output + (LETTERS[newindex])
    return(output)
    
    def LFSR_gen(seed, length):
    keystream_length = 0
    lfsr_array = []
    keystream = ""
    
    lfsr_array.append(seed)
    
    for i in range(1, length):
        bOne = lfsr_array[i - 1][3]
        bTwo = lfsr_array[i - 1][2]
        bThree = lfsr_array[i - 1][1]
        bFour = lfsr_array[i - 1][0]
        bFiveNew = str(int(lfsr_array[i - 1][4])^int(lfsr_array[i - 1][3])^int(lfsr_array[i - 1][1]))
        
        
        lfsr_array.append(bFiveNew + bFour + bThree + bTwo + bOne)
        
    for i in lfsr_array:
        keystream += i[-1]
    return keystream
    
    def LFSR_encipher(message, seed, encipher = True, LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ,.?!@#"):
    word = ''
    message = text_clean(message)
    xor_key = LFSR_gen(seed, 15)
    binh = binary_convert(message)
    if(encipher):
        word = xor_function(binh, xor_key)
        word = roman_convert(word).upper()
    else:
        word = xor_function(binh, xor_key)
        word = roman_convert(word).lower()
    return word
    
