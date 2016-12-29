Pytesser
========

Python wrapper for the tesseract OCR engine. The module is based on OpenCV.


Informations
------------

There is already multiples tesseract python modules, but none of them satisfied me. This one is different on the following point:

* All the classes are put in the same file and all inessential class are removed
* Use OpenCV instead of PIL (to really an advantage because PIL as far more widespread, but better fit my needs ;))
* Use subprocess.communicate instead of subprocess.wait to avoid any output in the shell or in the programs that use the module.
* Management of the differents languages via the option '-l' because the original pytesser use the default language which is english. By this way the detection of french for instance is totally inacurrate.
* Management of of the pagesegmode, which allow to modify the behavior of tesseract if we want for instance to detect only one character, a word or a line.
* The code is far more straightforward (my opinion)

How to use it ?
---------------

There is to ways to use it. Either you give it a filename, either directly an IplImage. For a filename you can do:

    import pytesser
    txt = pytesser.image_to_string("myimage.jpg") #By default language is eng, and page seg mode auto

    #To give specifify parameters:
    txt = pytesser.image_to_string("myimage.jpg","fra",pytesser.PSM_SINGLE_WORD) #Analyse image as a single french word


Or you can directly give it an IplImage like this:

    image = cv.LoadImage("myimage.jpg")
    txt = pytesser.iplimage_to_string(image) 

Or give it a mat:

    image = cv2.imwrite("myimage.jpg")
    txt = pytesser.mat_to_string(image) 
    
    

Improve
------------
* convert image image to gray scale before OCR
