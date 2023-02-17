
# Compile a java file
```javac -cp src_folder src/SourceFileWEntrypoint.java ```

or better 
```javac -sourcepath src -d classes src/SourceFileWEntrypoint.java```

# Run a compiled class file
``` java -cp location_of_classfiles MainClassFileName```

 
**Important: Do not add the .class extension for MainClassFileName!**

# Build a .jar file
First compile your project to a predefined output directory


```javac -sourcepath src -d out src/SourceFileWEntrypoint.java```


Enter the output dir

```cd out ```

Create a file Manifest.txt containting

```Main-Class: SourceFileWEntrypoint```

In that very directory (important!) run

``` jar cvmf Manifest.txt Jarname.jar SourceFileWEntrypoint.class  * ```

If the code needs any resources they also need to be in out, and be referenced correctly in the code

# Referencing resources within a .jar file in java code

In the folder which holds all the files to be zipped to a .jar, make sure that your resource files (e.g. images) are in the same directory as the class file needing to access these resources.

Then within an object method, to access your resource, e.g. ```Image.png```, you call

```
import javax.imageio.ImageIO;

...

String imageName = "Image.png";
source = ImageIO.read(getClass().getResourceAsStream(imageName));
```

or, if the calling method happens to be static

```
source = ImageIO.read(Assets.class.getResourceAsStream(imageName));
```

  
