---
title: "Introducción a los proyectos y soluciones en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b757178f29439f162df9e8844ae65ed8df642bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-projects-and-solutions"></a>Inicio rápido: proyectos y soluciones

En este tutorial rápido de 10 minutos de duración veremos qué significa crear una solución y un proyecto en Visual Studio. Echaremos un vistazo a las propiedades de un proyecto y a algunos de los archivos que puede contener. También crearemos una referencia a un segundo proyecto.

> [!TIP]
> En este inicio rápido crearemos una solución y un proyecto desde cero a modo de ejercicio educativo para comprender el concepto de proyecto. En su uso cotidiano de Visual Studio, al crear un proyecto seguramente recurra a una de las numerosas plantillas de proyecto que Visual Studio ofrece.

> [!NOTE]
> No hacen falta soluciones ni proyectos para desarrollar aplicaciones en Visual Studio. Basta con abrir una carpeta que contenga código para empezar a codificar, compilar y depurar. Por ejemplo, si clona un repositorio de GitHub, podría no contener soluciones y proyectos de Visual Studio. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluciones

Las soluciones son contenedores que Visual Studio usa para organizar uno o más proyectos relacionados. Cuando se abre una solución en Visual Studio, esta cargará automáticamente todos los proyectos que contiene.

### <a name="create-a-solution"></a>Crear una solución

Comenzaremos nuestro periplo creando una solución vacía. Cuando se familiarice con Visual Studio, lo más probable es que no cree soluciones vacías con demasiada frecuencia. Esto se debe a que, al crear un proyecto en Visual Studio, se crea automáticamente una solución donde se hospedará ese proyecto (si es que no hay ya una solución abierta).

1. Inicie Visual Studio.

   Visual Studio se abre y lo más seguro es que vea **Página de inicio** ocupando prácticamente todo el espacio de la ventana.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto...**

   Aparece el cuadro de diálogo **Nuevo proyecto** .

1. En el panel izquierdo, expanda **Otros tipos de proyectos** y seleccione **Soluciones de Visual Studio**. En el panel central, seleccione **Solución en blanco**. Denomine la solución "QuickSolution" y, luego, elija **Aceptar**.

   ![Plantilla de solución en blanco](media/quickstart-projects-new-solution.png)

   La **Página de inicio** se cierra y aparece una solución en el **Explorador de soluciones**, en el lado derecho de la ventana de Visual Studio. Seguramente use el **Explorador de soluciones** a menudo para examinar el contenido de los proyectos.

### <a name="add-a-project"></a>Agregar un proyecto

Ahora, agreguemos nuestro primer proyecto a la solución. Comenzaremos con un proyecto vacío y le agregaremos los elementos que necesitamos.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución 'QuickSolution'** en el **Explorador de soluciones**, elija **Agregar** > **Nuevo proyecto...**

   Se abre el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel izquierdo, expanda **Visual C#** y elija **Escritorio clásico de Windows**. Luego, en el panel central, elija **Proyecto vacío (.NET Framework)**. Asigne el nombre "QuickDate" al proyecto y, después, haga clic en el botón **Aceptar**.

   Un proyecto denominado "QuickDate" aparece debajo de la solución en el **Explorador de soluciones**. Actualmente solo contiene un archivo denominado **App.config**.

   > [!NOTE]
   > Si no ve **Visual C#** en el panel izquierdo del cuadro de diálogo, deberá instalar la carga de trabajo **Desarrollo de escritorio de .NET**. Una manera sencilla de llevar esto a cabo es haciendo clic en el vínculo **Abrir el instalador de Visual Studio** en la parte inferior de dicho panel izquierdo. El **Instalador de Visual Studio** se abre; desde allí, después de elegir la carga de trabajo correcta, seleccione el botón **Modificar**.

   ![Vínculo Abrir el instalador de Visual Studio](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Agregar un elemento al proyecto

Ya tenemos un proyecto vacío; ahora, vamos a agregar un archivo de código.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **QuickDate** en el **Explorador de soluciones**, elija **Agregar** > **Nuevo elemento...**

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. Expanda **Elementos de Visual C#** y elija **Código**. En el panel central, elija **Clase**. Denomine la clase "Calendar" y seleccione el botón **Agregar**.

   Un archivo denominado "Calendar.cs" se agrega al proyecto. El fragmento **.cs** del final es la extensión de archivo que tienen los archivos de código de C#. El archivo aparece en la jerarquía visual del proyecto en el **Explorador de soluciones** y su contenido se abre en el editor.

1. Reemplace el contenido del archivo **Calendar.cs** por el siguiente código.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   No es necesario comprender lo que hace el código, pero, si quiere, puede ejecutar el programa y ver que lo que realiza es imprimir la fecha de hoy en la ventana de consola.

## <a name="add-a-second-project"></a>Agregar un segundo proyecto

Es común que las soluciones contengan más de un proyecto y, a menudo, estos proyectos se hacen referencia entre sí. Algunos proyectos de una solución pueden ser bibliotecas de clases; otros, aplicaciones ejecutables, y otros, proyectos de prueba unitaria o sitios web.

Vamos a agregar un proyecto de prueba unitaria a la solución. Esta vez empezaremos con una plantilla de proyecto, por lo que no será necesario agregar otro archivo de código al proyecto.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución 'QuickSolution'** en el **Explorador de soluciones**, elija **Agregar** > **Nuevo proyecto...**

   Se abre el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel izquierdo, expanda **Visual Basic** y elija la categoría **Prueba**. En el panel central, elija **Proyecto de prueba unitaria (.NET Framework)**. Denomine el proyecto "QuickTest" y, después, seleccione el botón **Aceptar**.

   Se agregará un segundo proyecto al **Explorador de soluciones**, mientras que un archivo denominado **UnitTest1.vb** se abre en el editor. El fragmento **.vb** es la extensión de archivo de los archivos de código de Visual Basic.

   ![Explorador de soluciones con dos proyectos](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Agregar una referencia de proyecto

Usaremos el nuevo proyecto de prueba unitaria para probar nuestro método en el proyecto **QuickDate**, por lo que necesitamos agregar una referencia a ese proyecto. Esto crea una dependencia de compilación entre ambos proyectos, lo que significa que **QuickDate** se compilará antes que **QuickTest** cuando la solución se compile.

1. Elija el nodo **Referencias** en el proyecto **QuickTest** y, en el menú contextual que aparece al hacer clic con el botón derecho, elija **Agregar referencia...**

   ![Menú Agregar referencia](media/quickstart-projects-add-reference.png)

   Se abre el cuadro de diálogo **Administrador de referencias**.

1. En el panel izquierdo, expanda **Proyectos** y elija **Solución**. En el panel central, active la casilla junto a **QuickDate** y, después, seleccione el botón **Aceptar**.

   Se agrega una referencia al proyecto **QuickDate**.

## <a name="add-test-code"></a>Agregar código de prueba

1. Ahora vamos a agregar código de prueba al archivo de código de Visual Basic. Reemplace el contenido del archivo **UnitTest1.vb** por el siguiente código.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Verá una línea ondulada de color rojo debajo de algunas partes del código. Solucionaremos este error cuando convirtamos el proyecto de prueba en un [ensamblado de confianza](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) del proyecto **QuickDate**.

1. En el proyecto **QuickDate**, abra el archivo **Calendar.cs** (si aún no está abierto) y agregue la siguiente instrucción Using y el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para resolver el error en el proyecto de prueba.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   El archivo de código debe tener este aspecto.

   ![Código de CSharp](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Propiedades del proyecto

La línea del archivo de código C# que contiene el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> hace referencia al nombre de ensamblado del proyecto **QuickTest**. El nombre del ensamblado no siempre es el mismo que el nombre del proyecto. Para averiguar el nombre del ensamblado de un proyecto, abra las propiedades del proyecto.

1. En el **Explorador de soluciones**, seleccione el proyecto **QuickTest**. En el menú contextual que se abre al hacer clic con el botón derecho, seleccione **Propiedades** o, simplemente, presione **Alt**+**ENTRAR**.

   Las páginas de propiedades del proyecto se abren en la pestaña **Aplicación**. Fíjese en que el nombre de ensamblado del proyecto **QuickTest** es, efectivamente, "QuickTest". Si quisiera cambiarlo, aquí es donde lo haría. Así, cuando compile el proyecto de prueba, el nombre del archivo ejecutable resultante cambiaría de **QuickTest.exe** a lo que haya elegido.

   ![Propiedades del proyecto](media/quickstart-projects-properties.png)

1. Explore algunas de las otras pestañas de las páginas de propiedades del proyecto, como **Compilar** y **Configuración**. Estas pestañas serán distintas dependiendo del tipo de proyecto.

## <a name="next-steps"></a>Pasos siguientes

Si quiere comprobar que la prueba unitaria funciona, seleccione **Probar** > **ejecutar** > **Todas las pruebas** desde la barra de menús. Se abre una ventana denominada **Explorador de pruebas**, donde debería ver que la prueba **TestGetCurrentDate** se supera.

¡Enhorabuena por completar este tutorial de inicio rápido! Tras esto, puede que quiera explorar algunos de los demás inicios rápidos sobre Visual Studio u obtener más información sobre cómo [crear proyectos y soluciones](../ide/creating-solutions-and-projects.md).

## <a name="see-also"></a>Vea también

[Guía de inicio rápido: Primer vistazo al IDE de Visual Studio](../ide/quickstart-ide-orientation.md)  
[Guía de inicio rápido: Personalizar el IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Inicio rápido: escribir código en el editor](../ide/quickstart-editor.md)  
[Administrar propiedades de soluciones y proyectos](../ide/managing-project-and-solution-properties.md)  
[Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)  
[Desarrollar código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)  
[Introducción al IDE de Visual Studio](../ide/visual-studio-ide.md)
