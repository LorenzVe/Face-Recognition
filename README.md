# Face-Recognition
Defining some Converters for JPEG, JPEG2000, JPEG-XR and a face recognition software

## Documentation 
	
### 14-March-2021:
Bearbeitet werden die Punkte (0) und (1) von der Aufgabenstellung zu * *Multimedia Datenformate* *.
1. (0) Get software for JPEG, JPEG2000, JPRG XR and use it for compressing images to a fixed file size (compression ratio).
   - **JPEG**: JpegOptim, JPEG-recompress, ...
     - Jpegoptim ist ein Kommandozeilen-Programm für Linux und Windows
       ```
       $jepegoptim --size=100k --dest=<Output> <image1.jpeg>
       ```
     - Result: .jpg   
     - Keine Qualitätsverlust
     - Quelldatei wird standardmäßig überschrieben
     - Optimization: bis zu 70% durch eine Optimierung der Huffmann-Tabellen (Codewörter der Quelle, Präfixcode)
     - entfernt folgende Daten aus der Ausgabedatei:
       - **IPTC**: International Press Telecommunications Council
       - **XMP**: Extensible Metadata Platform
       - **ICC**: International Color Consortium
     - beibehält Standardmäßig folgende Daten:
       - **Exif**: Exchangeable Image File Format
       - **Com**: Comment/kommentare
     - ```--strip-all```: Entfernt alle Daten aus der Ausgabedatei.
       - **-m**: Kompress-Methode angeben
     - Rekursives Bearbeiten aller JPEG-Dateien:
       - **Linux**:
         ```
         $find -type f -name "*.jpg" -exec jpegoptim -p -P --strip-all {} \;
         ```
       - **Windows**:
         ```
         $for /R %%i in (*.jpg) do "R:\jpegoptim.exe" -p -P --strip-all "%%i"
         ```
     - **Links**:
       - [Github: tjko/jpegoptim](https://github.com/tjko/jpegoptim)
       - [Thorste Willert](https://www.thorsten-willert.de/optimierung/grafikoptimierung/jpeg-dateien-optimieren-mit-jpegoptim)
     - ```mogrify -extent 300x100 -gravity Center image.jpg```

   - **JPEG2000**: OpenJPEG (opj_compress, opj_decompress)
     - **opj_compress**:
       - Konvertiert .bmp, .pgm, .pgx, .png, .pnm, .ppm, .raw, .tga, .tif --> .j2k, .jp2, .j2c, .jpt
       ```
       $opj compress -r <Size> -i <File> -o newFileName
       ```
     - **opj_decompress**:
       - Konvertiert .j2k, .jp2, .j2c, .jpt --> .bmp, .pgm, .pgx, .png, .pnm, .ppm, .raw, .tga, .tif
       ```
       $opj decompress -r <Size> -i <File> -o newFileName
       ```
     - Bessere Komprimierungsrate bei gegebener Qualität
     - mehr bei [openjpeg-wiki](https://github.com/uclouvain/openjpeg/wiki/DocJ2KCodec)

   - **JPEG XR**: JxrEncApp, NCH Software
     - JxrEncApp: JPEG XR Encoder Utility - Microsoft
       - .bmp, .tif, .hdr --> .jxr
       - JxrEncApp -i <inputFile> -o <outputFile> -q <[0.0 - 1.0) oder [1 - 255]>
       - Example: 
         ```
         JxrEncApp -i input.bmp -o output.jxr -q 10 
         ```
     - mehr bei [ubuntu-manpage](http://manpages.ubuntu.com/manpages/bionic/man1/JxrEncApp.1.html).
   - **Some other** software which contain two or more convert methods can be found below
     - We have discovered some online converter tools which can be accessed with the following links
       - [Onlineconvert](https://www.onlineconvert.com/jpg-to-jxr)
       - [Aconvert](https://www.aconvert.com/image/jpg-to-jp2/)
     - and a downloadable Software which covers all convert techniques listed before
       - [NCH-Software](https://www.nchsoftware.com/imageconverter/index.html) 

2. (1) Define face recognition system + dataset and learn to use it.
   - **Datasets**
     - The datasets are stored locally.
     - We used the data downloaded from the following Websites (names are used to better identify between them for ourselves):
       - [Caltech](http://www.vision.caltech.edu/html-files/archive.html)
       - [Robotics](http://robotics.csie.ncku.edu.tw/Databases/FaceDetect_PoseEstimate.htm)
       - [Kaggle](https://www.kaggle.com/atulanandjha/lfwpeople)
    
