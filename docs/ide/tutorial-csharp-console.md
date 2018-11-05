---
title: Introducción a las aplicaciones de consola de C# en Visual Studio
description: Aprenda a crear una aplicación de consola de C# en Visual Studio mediante un procedimiento paso a paso.
ms.custom: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 3450572e4cf4959530599c5eea9efb3168485b58
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244377"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutorial: Introducción a la aplicación de consola de C# en Visual Studio

En este tutorial para C#, usará Visual Studio para crear y ejecutar una aplicación de consola y explorar algunas características del [entorno de desarrollo integrado (IDE) de Visual Studio](visual-studio-ide.md) mientras lo hace.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, crearemos un proyecto de aplicación C#. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **Nuevo proyecto** del panel de la izquierda, expanda **C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Después, asigne el nombre *Calculator* al archivo.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Agregar un grupo de trabajo (opcional)

Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, puede obtenerla si agrega la carga de trabajo **Desarrollo multiplataforma de .NET Core**. Puede agregar esta carga de trabajo de una de las dos formas siguientes, según las actualizaciones de Visual Studio 2017 que estén instaladas en el equipo.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Usar el cuadro de diálogo Nuevo proyecto

1. Elija el vínculo **Abrir el Instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**.

   ![Elija el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Usar la barra del menú Herramientas

1. Cancele para salir del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, seleccione **Herramientas** > **Obtener herramientas y características...**.

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

## <a name="create-a-c-console-calculator-app"></a>Creación de una aplicación "C# Console Calculator"

1. Después de crear la **Aplicación de consola de C#**, escriba o pegue el código siguiente en el editor de código:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   El código que aparece después de `static void Main(string[] args)` debe ser similar a la captura de pantalla siguiente:

   ![Editor de código que muestra la aplicación C# Console Calculator](../ide/media/csharp-console-calculator-code.png)

1. Elija **Calculator** para ejecutar el programa, o bien presione **F5**.

   ![Elección del botón Calculator para ejecutar la aplicación desde la barra de herramientas](../ide/media/csharp-console-calculator-button.png)

1. Vea la aplicación en la ventana de la consola. Al seguir las indicaciones, la aplicación debe tener un aspecto similar a la captura de pantalla siguiente:

    ![Ventana de consola en la que se muestra la aplicación Calculator, que incluye mensajes sobre las acciones que se deben realizar.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Cierre la aplicación

1. Presione cualquier tecla para cerrar la aplicación Calculator.

1. Cierre el panel **Salida** en Visual Studio.

   ![Cierre del panel Salida en Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Cierre Visual Studio.

## <a name="quick-answers-faq"></a>Respuestas rápidas a preguntas frecuentes

Esta es una sección rápida de P+F para destacar algunos conceptos clave.

### <a name="what-is-c"></a>¿Qué es C#?

C# es un lenguaje de programación con seguridad de tipos que se ejecuta en .NET Framework y .NET Core. Con C#, puede crear aplicaciones Windows, aplicaciones cliente-servidor, aplicaciones de base de datos, servicios web XML, componentes distribuidos, etc.

### <a name="what-is-visual-studio"></a>¿Qué es Visual Studio?

Visual Studio es un conjunto de desarrollo integrado de herramientas de productividad para desarrolladores. Considérelo como un programa que se puede usar para crear programas y aplicaciones.

### <a name="what-is-a-console-app"></a>¿Qué es una aplicación de consola?

Una aplicación de consola toma la entrada y muestra la salida en una ventana de línea de comandos, también conocida como consola.

### <a name="what-is-net-core"></a>¿Qué es .NET Core?

.NET core es el siguiente paso evolutivo de .NET Framework. Donde .NET Framework permitía compartir código entre lenguajes de programación, .NET Core agrega la capacidad de compartir código entre plataformas. Y todavía mejor, es de código abierto.

(Tanto .NET Framework como .NET Core incluyen bibliotecas de funcionalidad creada previamente. También incluyen un Common Language Runtime (CLR), que actúa como una máquina virtual en la que se va a ejecutar el código).

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Para más información, continúe con los tutoriales siguientes.

> [!div class="nextstepaction"]
> [Tutoriales de C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Vea también

* [Curso en vídeo de aspectos básicos de C# para principiantes sin experiencia](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
