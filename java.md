
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

  
