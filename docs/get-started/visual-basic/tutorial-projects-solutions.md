---
title: 'Tutorial: Soluciones y proyectos de Visual Basic'
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 124d27b5dc139e57f9041694afe42d42eef03fb5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58069624"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Información sobre proyectos y soluciones con Visual Basic

En este artículo introductorio se explica qué significa crear una *solución* y un *proyecto* en Visual Studio. Una solución es un contenedor que se usa para organizar uno o más proyectos de código relacionados, por ejemplo, un proyecto de biblioteca de clases y un proyecto de prueba correspondiente. Echaremos un vistazo a las propiedades de un proyecto y a algunos de los archivos que puede contener. También se crea una referencia de un proyecto a otro.

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalarlo de forma gratuita.

Se crean una solución y un proyecto desde cero como ejercicio educativo para comprender el concepto de proyecto. Cuando use Visual Studio, es probable que emplee alguna de las distintas *plantillas* de proyecto que Visual Studio ofrece al crear un nuevo proyecto.

> [!NOTE]
> No hacen falta soluciones ni proyectos para desarrollar aplicaciones en Visual Studio. Basta con abrir una carpeta que contenga código para empezar a codificar, compilar y depurar. Por ejemplo, si clona un repositorio de [GitHub](https://github.com/), podría no contener soluciones y proyectos de Visual Studio. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Soluciones y proyectos

A pesar de su nombre, una solución no es una "respuesta", sino simplemente contenedores que Visual Studio usa para organizar uno o más proyectos relacionados. Cuando se abre una solución en Visual Studio, esta carga automáticamente todos los proyectos que la solución contiene.

### <a name="create-a-solution"></a>Crear una solución

Comenzaremos nuestro periplo creando una solución vacía. Cuando se familiarice con Visual Studio, lo más probable es que no cree soluciones vacías con mucha frecuencia. Al crear un proyecto, Visual Studio crea automáticamente una solución para hospedar ese proyecto si es que no hay ya una solución abierta.

::: moniker range="vs-2017"

1. Abra Visual Studio.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

   Aparece el cuadro de diálogo **Nuevo proyecto** .

1. En el panel izquierdo, expanda **Otros tipos de proyectos** y seleccione **Soluciones de Visual Studio**. En el panel central, elija la plantilla **Solución en blanco**. Denomine la solución **QuickSolution** y, luego, elija **Aceptar**.

   ![Plantilla Solución en blanco en Visual Studio](../media/tutorial-projects-new-solution.png)

   La **página de inicio** se cierra y aparece una solución en el **Explorador de soluciones**, en el lado derecho de la ventana de Visual Studio. Seguramente use el **Explorador de soluciones** a menudo para examinar el contenido de los proyectos.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. En la página **Crear un proyecto nuevo**, escriba **solución en blanco** en el cuadro de búsqueda, seleccione la plantilla **Solución en blanco** y elija **Siguiente**.

4. Asígnele a la solución el nombre **QuickSolution** y elija **Crear**.

   Aparece una solución en el **Explorador de soluciones**, en el lado derecho de la ventana de Visual Studio. Seguramente use el **Explorador de soluciones** a menudo para examinar el contenido de los proyectos.

::: moniker-end

### <a name="add-a-project"></a>Agregar un proyecto

Ahora, agreguemos nuestro primer proyecto a la solución. Comenzaremos con un proyecto vacío y le agregaremos los elementos que necesitamos.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución "QuickSolution"** en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo proyecto**.

   Se abre el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel izquierdo, expanda **Visual Basic** y elija **Escritorio de Windows**. Luego, en el panel central, elija la plantilla **Proyecto vacío (.NET Framework)**. Asigne el nombre **QuickDate** al proyecto y luego haga clic en el botón **Aceptar**.

   Un proyecto denominado QuickDate aparece debajo de la solución en el **Explorador de soluciones**. Actualmente solo contiene un archivo denominado *App.config*.

   > [!NOTE]
   > Si no ve **Visual Basic** en el panel izquierdo del cuadro de diálogo, debe instalar la *carga de trabajo* de **desarrollo de escritorio de .NET** de Visual Studio. Visual Studio usa la instalación basada en la carga de trabajo para instalar únicamente los componentes necesarios para el tipo de desarrollo que lleva a cabo. Una manera sencilla de instalar una nueva carga de trabajo es hacer clic en el vínculo **Abrir el instalador de Visual Studio** en la esquina inferior izquierda del cuadro de diálogo **Agregar nuevo proyecto**. Una vez que se abra el Instalador de Visual Studio, elija la carga de trabajo de **desarrollo de escritorio de .NET** y luego haga clic en el botón **Modificar**.

   ![Vínculo Abrir el instalador de Visual Studio](media/tutorial-projects-open-installer-vb.png)

## <a name="add-an-item-to-the-project"></a>Agregar un elemento al proyecto

Hay un proyecto vacío. Vamos a agregar un archivo de código.

1. En el menú contextual que aparece al hacer clic con el botón derecho en el proyecto **QuickDate** del **Explorador de soluciones**, elija **Agregar** > **Nuevo elemento**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. Expanda **Elementos comunes** y elija **Código**. En el panel central, elija la plantilla de proyecto **Clase**. Ponga el nombre **Calendar** a la clase y luego haga clic en el botón **Agregar**.

   Un archivo denominado *Calendar.vb* se agrega al proyecto. El fragmento *.vb* del final es la extensión de archivo de los archivos de código de Visual Basic. El archivo aparece en la jerarquía visual del proyecto en el **Explorador de soluciones** y su contenido se abre en el editor.

1. Reemplace el contenido del archivo *Calendar.vb* por el siguiente código:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   La clase `Calendar` contiene una sola función, `GetCurrentDate`, que devuelve la fecha actual.

1. Abra las propiedades del proyecto haciendo doble clic en **Mi proyecto** en el **Explorador de soluciones**. En la pestaña **Aplicación**, cambie **Tipo de aplicación** por **Biblioteca de clases**. Este paso es necesario para compilar el proyecto correctamente.

1. Compile el proyecto haciendo clic con el botón derecho en **QuickDate** en el **Explorador de soluciones** y seleccionando **Compilar**. Debería aparecer un mensaje de compilación correcta en la ventana **Resultados**.

## <a name="add-a-second-project"></a>Agregar un segundo proyecto

Es común que las soluciones contengan más de un proyecto y, a menudo, estos proyectos se hacen referencia entre sí. Algunos proyectos de una solución pueden ser bibliotecas de clases; otros, aplicaciones ejecutables, y otros, proyectos de prueba unitaria o sitios web.

Vamos a agregar un proyecto de prueba unitaria a la solución. Esta vez se empieza a partir de una plantilla de proyecto, así que no es necesario agregar otro archivo de código al proyecto.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución "QuickSolution"** en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo proyecto**.

   Se abre el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel izquierdo, expanda **Visual Basic** y elija la categoría **Prueba**. En el panel central, elija la plantilla de proyecto **Proyecto de prueba unitaria (.NET Framework)**. Ponga el nombre **QuickTest** al proyecto y luego haga clic en el botón **Aceptar**.

   Se agregará un segundo proyecto al **Explorador de soluciones**, mientras que un archivo denominado *UnitTest1.vb* se abre en el editor.

   ![Explorador de soluciones de Visual Studio con dos proyectos](media/tutorial-projects-solution-explorer-vb.png)

## <a name="add-a-project-reference"></a>Agregar una referencia de proyecto

Usaremos el nuevo proyecto de prueba unitaria para probar nuestro método en el proyecto **QuickDate**, por lo que necesitamos agregar una referencia a ese proyecto. Esto crea una *dependencia de compilación* entre ambos proyectos, lo que significa que, al compilar la solución, **QuickDate** se compila antes que **QuickTest**.

1. Seleccione el nodo **Referencias** en el proyecto **QuickTest** y, en el menú contextual que aparece al hacer clic con el botón derecho, seleccione **Agregar referencia**.

   ![Menú Agregar referencia](media/tutorial-projects-add-reference-vb.png)

   Se abre el cuadro de diálogo **Administrador de referencias**.

1. En el panel izquierdo, expanda **Proyectos** y elija **Solución**. En el panel central, active la casilla junto a **QuickDate** y, después, seleccione el botón **Aceptar**.

   Se agrega una referencia al proyecto **QuickDate**.

## <a name="add-test-code"></a>Agregar código de prueba

1. Ahora vamos a agregar código de prueba al archivo de código de Visual Basic. Reemplace el contenido del archivo *UnitTest1.vb* por el siguiente código.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Verá una línea ondulada de color rojo debajo de algunas partes del código. Solucionaremos este error cuando convirtamos el proyecto de prueba en un [ensamblado de confianza](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) del proyecto **QuickDate**.

1. En el proyecto **QuickDate**, abra el archivo *Calendar.vb*, si aún no está abierto, y agregue la siguiente [instrucción Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) y el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para resolver el error en el proyecto de prueba.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   El archivo de código debe tener este aspecto:

   ![código de Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Propiedades del proyecto

La línea del archivo *Calendar.vb* que contiene el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> hace referencia al nombre de ensamblado (nombre de archivo) del proyecto **QuickTest**. El nombre del ensamblado no siempre es el mismo que el nombre del proyecto. Para averiguar el nombre del ensamblado de un proyecto, abra las propiedades del proyecto.

1. En el **Explorador de soluciones**, seleccione el proyecto **QuickTest**. En el menú contextual que se abre al hacer clic con el botón derecho, seleccione **Propiedades** o, simplemente, presione **Alt**+**ENTRAR**. (También puede hacer doble clic en **Mi proyecto** en el **Explorador de soluciones**).

   Las *páginas de propiedades* del proyecto se abren en la pestaña **Aplicación**. Las páginas de propiedades contienen varios valores para el proyecto. Fíjese en que el nombre de ensamblado del proyecto **QuickTest** es, efectivamente, "QuickTest". Si quisiera cambiarlo, aquí es donde lo haría. Así, al compilar el proyecto de prueba, el nombre del archivo binario resultante cambiaría de *QuickTest.dll* a lo que hubiera elegido.

   ![Propiedades del proyecto](../media/tutorial-projects-properties.png)

1. Explore algunas de las otras pestañas de las páginas de propiedades del proyecto, como **Compilar** y **Configuración**. Estas pestañas son diferentes para los distintos tipos de proyectos.

## <a name="optional-run-the-test"></a>(Opcional) Ejecutar la prueba

Si quiere comprobar que la prueba unitaria funciona, seleccione **Probar** > **ejecutar** > **Todas las pruebas** desde la barra de menús. Se abre una ventana denominada **Explorador de pruebas**, donde debería ver que la prueba **TestGetCurrentDate** se supera.

![Explorador de pruebas de Visual Studio que muestra una prueba correcta](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Si la ventana **Explorador de pruebas** no se abre automáticamente, ábrala al elegir **Prueba** > **Windows** > **Explorador de pruebas** en la barra de menús.

## <a name="next-steps"></a>Pasos siguientes

Si desea seguir explorando Visual Studio, considere la posibilidad de crear una aplicación siguiendo uno de los [tutoriales de Visual Basic](index.yml).

## <a name="see-also"></a>Vea también

- [Crear proyectos y soluciones](../../ide/creating-solutions-and-projects.md)
- [Administración de propiedades de soluciones y proyectos](../../ide/managing-project-and-solution-properties.md)
- [Administración de referencias en un proyecto](../../ide/managing-references-in-a-project.md)
- [Desarrollar código en Visual Studio sin proyectos o soluciones](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Introducción al IDE de Visual Studio](../../get-started/visual-studio-ide.md)