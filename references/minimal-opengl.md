---
layout: page
active: references
title: "Minimal OpenGL Example"
auto-title: true
---


A (hopefully) compiling version of this example can be found [here](https://github.com/iondune/MinimalOpenGLExample).


### Vertex Shader

```glsl
#version 330

in vec2 position;

void main()
{
    gl_Position = vec4(position, 0.0, 1.0);
};
```

### Fragment Shader

```glsl
#version 330

out vec4 outColor;

void main()
{
    outColor = vec4(1.0, 1.0, 1.0, 1.0);
}
```

### Source

```cpp
#include <glad/glad.h>
#include <GLFW/glfw3.h>
#include <iostream>


// Helper function to print out the compiler errors from GLSL
void PrintShaderInfoLog(GLint const Shader)
{
    int InfoLogLength = 0;
    int CharsWritten = 0;

    glGetShaderiv(Shader, GL_INFO_LOG_LENGTH, & InfoLogLength);

    if (InfoLogLength > 0)
    {
        GLchar * InfoLog = new GLchar[InfoLogLength];
        glGetShaderInfoLog(Shader, InfoLogLength, & CharsWritten, InfoLog);
        std::cout << "Shader Info Log:" << std::endl << InfoLog << std::endl;
        delete [] InfoLog;
    }
}

int main()
{
    //////////////////////////////////
    // Create Window to render into //
    //////////////////////////////////

    GLFWwindow * window = nullptr;
    if (! glfwInit())
    {
        return -1;
    }

    window = glfwCreateWindow(640, 480, "Hello World", NULL, NULL);
    if (! window)
    {
        glfwTerminate();
        return -1;
    }

    glfwMakeContextCurrent(window);

    if (! gladLoadGL())
    {
        return -1;
    }


    //////////
    // Data //
    //////////

    // Load shader files
    char const * VertexShaderSource = LoadFromFile("shader.vert");
    char const * FragmentShaderSource = LoadFromFile("fragment.vert");

    // Vertex data
    GLfloat const Vertices[] = {
        0.0f,  0.5f,
        0.5f, -0.5f,
        -0.5f, -0.5f
    };

    // Index data
    GLuint const Indices[] = {
        0, 1, 2
    };


    ////////////////////
    // OpenGL Objects //
    ////////////////////

    // Create Vertex Array Object
    GLuint VAO;
    glGenVertexArrays(1, & VAO);
    glBindVertexArray(VAO);

    // Create Vertex Buffer Object
    GLuint VBO;
    glGenBuffers(1, & VBO);
    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(Vertices), Vertices, GL_STATIC_DRAW);
    glBindBuffer(GL_ARRAY_BUFFER, 0);

    // Create Index Buffer Object
    GLuint IBO;
    glGenBuffers(1, & IBO);
    glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, IBO);
    glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(Indices), Indices, GL_STATIC_DRAW);


    /////////////////////
    // Compile Shaders //
    /////////////////////

    // Compile vertex shader
    GLint Compiled;
    GLuint VertexShader = glCreateShader(GL_VERTEX_SHADER);
    glShaderSource(VertexShader, 1, & VertexShaderSource, NULL);
    glCompileShader(VertexShader);
    glGetShaderiv(VertexShader, GL_COMPILE_STATUS, & Compiled);
    if (! Compiled)
    {
        std::cerr << "Failed to compile vertex shader!" << std::endl;
        PrintShaderInfoLog(VertexShader);
    }

    // Compile fragment shader
    GLuint FragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
    glShaderSource(FragmentShader, 1, & FragmentShaderSource, NULL);
    glCompileShader(FragmentShader);
    glGetShaderiv(FragmentShader, GL_COMPILE_STATUS, & Compiled);
    if (! Compiled)
    {
        std::cerr << "Failed to compile fragment shader!" << std::endl;
        PrintShaderInfoLog(FragmentShader);
    }

    // Compile shader
    GLuint ShaderProgram = glCreateProgram();
    glAttachShader(ShaderProgram, VertexShader);
    glAttachShader(ShaderProgram, FragmentShader);
    glBindFragDataLocation(ShaderProgram, 0, "outColor");
    glLinkProgram(ShaderProgram);
    glUseProgram(ShaderProgram);

    // Enable the attribute from our VBO
    GLint PositionAttribute = glGetAttribLocation(ShaderProgram, "position");
    glEnableVertexAttribArray(PositionAttribute);

    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glVertexAttribPointer(PositionAttribute, 2, GL_FLOAT, GL_FALSE, 0, 0);
    glBindBuffer(GL_ARRAY_BUFFER, 0);


    ///////////////
    // Main Loop //
    ///////////////

    while (! glfwWindowShouldClose(window))
    {
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
        glDrawElements(GL_TRIANGLES, 3, GL_UNSIGNED_INT, 0);

        glfwSwapBuffers(window);
        glfwPollEvents();
    }


    /////////////
    // Cleanup //
    /////////////

    glDeleteProgram(ShaderProgram);
    glDeleteShader(FragmentShader);
    glDeleteShader(VertexShader);

    glDeleteBuffers(1, & IBO);
    glDeleteBuffers(1, & VBO);
    glDeleteVertexArrays(1, & VAO);

    return 0;
}

```
