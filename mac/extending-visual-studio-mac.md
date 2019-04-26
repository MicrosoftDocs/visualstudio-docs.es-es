---
title: Extender Visual Studio para Mac
description: Puede extender las características y las funciones de Visual Studio para Mac con módulos denominados paquetes de extensión. En la primera parte de esta guía, se crea un paquete de extensión simple de Visual Studio para Mac para insertar la fecha y hora en un documento. En la segunda parte de esta guía, se presentan los conceptos básicos del sistema de paquetes de extensión y algunas de las API principales que conforman la base de Visual Studio para Mac.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 3465ef29ca732cd26c03919082052d8b26a83ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983171"
---
# <a name="extending-visual-studio-for-mac"></a>Extender Visual Studio para Mac

Visual Studio para Mac consta de un conjunto de módulos denominados *paquetes de extensión*. Puede usar los paquetes de extensión para incluir una nueva función en Visual Studio para Mac, como la compatibilidad con un idioma adicional o una nueva plantilla de proyecto.

Los paquetes de extensión se compilan desde los puntos de *extensión* de otros paquetes de extensión. Los puntos de extensión son marcadores de posición para las áreas que se pueden expandir, por ejemplo, un menú o la lista de comandos del IDE. Puede compilar un paquete de extensión desde un punto de extensión. Para ello, registre un nodo de datos estructurados denominados extensiones, como un nuevo elemento de menú o un comando nuevo. Cada punto de extensión acepta ciertos tipos de extensiones, como *Command*, *Pad* o *FileTemplate*. Un módulo que contiene puntos de extensión se denomina *host de complemento*, ya que lo pueden extender otros paquetes de extensión.

Para personalizar Visual Studio para Mac, puede crear un paquete de extensión que se compile desde los puntos de extensión contenidos en hosts de complemento en las bibliotecas preexistentes de Visual Studio para Mac, como se muestra en el diagrama siguiente:

![Arquitectura de complementos](media/extending-visual-studio-mac-addin1.png)

Para que un paquete de extensión se compile desde Visual Studio para Mac, debe tener extensiones que se compilen desde puntos de extensión preexistentes en el IDE de Visual Studio para Mac. Cuando un paquete de extensión se basa en un punto de extensión definido en un host de complemento, se dice que tiene una  _dependencia_  en ese paquete de extensión.

La ventaja de este diseño modular es que Visual Studio para Mac es extensible, ya que hay muchos puntos de extensión desde los que se puede compilar con paquetes de extensión personalizados. Entre los ejemplos de paquetes de extensión actuales se incluyen la compatibilidad con C# y F#, las herramientas del depurador y las plantillas de proyecto.

> [!NOTE]
> **Nota**: Si tiene un proyecto de Add-in Maker creado antes de Add-in Maker 1.2, debe migrar el proyecto siguiendo los pasos que se describen [aquí](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

En esta sección se examinan los diferentes archivos que genera Add-in Maker y los datos que requiere una extensión de comando.

## <a name="attribute-files"></a>Archivos de atributos

Los paquetes de extensión almacenan metadatos sobre el nombre, la versión, las dependencias y otra información en atributos de C#. Add-in Maker crea dos archivos, `AddinInfo.cs` y `AssemblyInfo.cs`, para almacenar y organizar esta información. Los paquetes de extensión deben tener un identificador y un espacio de nombres únicos especificados en el *atributo Addin*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Los paquetes de extensión también deben declarar las dependencias en los paquetes de extensión que poseen los puntos de extensión a los que se conectan. Se hace referencia a estos automáticamente en tiempo de compilación.

Además, se pueden agregar referencias adicionales a través del nodo de referencias de complemento en el panel de solución del proyecto, como se muestra en la imagen siguiente:

![Captura de pantalla de insertar fecha](media/extending-visual-studio-mac-addin13.png)

También se agregan sus atributos `assembly:AddinDependency` correspondientes en tiempo de compilación. Una vez que se han colocado los metadatos y las declaraciones de dependencias, puede centrarse en los bloques de creación fundamentales del paquete de extensión.

## <a name="extensions-and-extension-points"></a>Extensiones y puntos de extensión

Un punto de extensión es un marcador de posición que define una estructura de datos (un tipo), mientras que una extensión define los datos que se ajustan a una estructura especificada por un punto de extensión específico. Los puntos de extensión especifican qué tipo de extensión pueden aceptar en su declaración. Las extensiones se declaran mediante nombres de tipo o rutas de acceso de extensión. Vea la [referencia sobre los puntos de extensión](https://github.com/mono/mono-addins/wiki/Extension-Points) para obtener una explicación más detallada sobre cómo crear el punto de extensión que necesita.

La arquitectura de extensión/punto de extensión garantiza que el desarrollo de Visual Studio para Mac sea rápido y modular.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Extensiones de comando

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Las extensiones de comando son extensiones que apuntan a los métodos a los que se llama cada vez que se ejecutan.

Las extensiones de comando se definen mediante la adición de entradas al punto de extensión `/MonoDevelop/Ide/Commands`. Hemos definido nuestra extensión en `Manifest.addin.xml` con el código siguiente:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

El nodo de extensión contiene un atributo de ruta de acceso que especifica el punto de extensión al que se conecta, en este caso, `/MonoDevelop/Ide/Commands/Edit`. Además, actúa como nodo primario para el comando. El nodo de comando tiene los atributos siguientes:

* **id**: especifica el identificador de este comando. Los identificadores de comando deben declararse como miembros de enumeración y se usan para conectar Commands a CommandItems.
* **_label**: texto que se mostrará en los menús.
* **_description**: texto que se mostrará como una información sobre herramientas para los botones de la barra de herramientas.
* **defaultHandler**: especifica la clase `CommandHandler` que activa el comando.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

En el siguiente fragmento de código se muestra una extensión de CommandItem que se conecta al punto de extensión `/MonoDevelop/Ide/MainMenu/Edit`:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem coloca un comando especificado en su atributo id en un menú. Dicho CommandItem extiende el punto de extensión `/MonoDevelop/Ide/MainMenu/Edit`, lo que hace que la etiqueta del comando aparezca en el **menú Edición**. Tenga en cuenta que el valor de **id** de CommandItem se corresponde con el identificador del nodo de comandos, `InsertDate`. Si quita CommandItem, la opción **Insertar fecha** desaparecerá del menú Edición.

### <a name="command-handlers"></a>Controladores de comandos

`InsertDateHandler` es una extensión de la clase `CommandHandler`. Reemplaza dos métodos, `Update` y `Run`. El método `Update` se consulta cada vez que un comando se muestra en un menú o se ejecuta mediante enlaces de teclado. Al cambiar el objeto de información, puede deshabilitar el comando o convertirlo en invisible, rellenar comandos de matriz, etc. El método `Update` deshabilita el comando si no encuentra un objeto *Document* activo con un objeto *TextEditor* en el que insertar texto:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Solo necesita invalidar el método `Update` cuando tiene una lógica especial para habilitar u ocultar el comando. El método `Run` se ejecuta cada vez que un usuario ejecuta un comando, lo que en este caso se produce cuando un usuario selecciona el comando en el menú Edición. Este método inserta la fecha y hora en el símbolo de inserción en el editor de texto:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Declare el tipo Command como un miembro de enumeración en `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Esto enlaza Command y CommandItem y, cuando en el **menú Edición** se selecciona CommandItem, este llama a Command.

## <a name="ide-apis"></a>API del IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Para obtener información sobre el ámbito de las áreas disponibles para el desarrollo, vea [Extension Tree Reference](http://monodevelop.com/Developers/Articles/Extension_Tree_Reference) (Referencia del árbol de extensión) y [API Overview](http://monodevelop.com/Developers/Articles/API_Overview) (Introducción a la API). Al compilar paquetes de extensión avanzados, vea también los [artículos para desarrolladores](http://monodevelop.com/Developers/Articles). A continuación se muestra una lista parcial de las áreas que se pueden personalizar:

* Paneles
* Esquemas de enlace del teclado
* Directivas
* Formateadores de código
* Formatos de archivos de proyecto
* Paneles de preferencias
* Paneles de opciones
* Protocolos del depurador
* Visualizadores del depurador
* Diseños del área de trabajo
* Nodos de árbol del panel de soluciones
* Márgenes del editor de código fuente
* Motores de prueba unitaria
* Generadores de código
* Fragmentos de código
* Versiones de .NET Framework de destino
* Tiempo de ejecución de destino
* Back-end de VCS
* Refactorización
* Controladores de ejecución
* Resalte de sintaxis

## <a name="additional-information"></a>Información adicional

> [!NOTE]
> Actualmente estamos trabajando para mejorar los escenarios de extensibilidad de Visual Studio para Mac. Si está creando extensiones y necesita más información o ayuda, o si quiere proporcionar comentarios, rellene el formulario [Visual Studio for Mac Extension Authoring](https://aka.ms/vsmac-extensions-survey) (Creación de extensiones de Visual Studio para Mac).

## <a name="see-also"></a>Vea también

- [Comenzar a desarrollar extensiones de Visual Studio (en Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)