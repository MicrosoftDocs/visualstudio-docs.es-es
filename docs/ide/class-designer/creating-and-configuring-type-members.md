---
title: Crear y configurar miembros de tipo (Diseñador de clases)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfed51812b034d63f250a56548b88f09a98214fe
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590415"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Crear y configurar miembros de tipo en el Diseñador de clases

Puede agregar estos miembros a los tipos en un diagrama de clase y configurarlos en la ventana **Detalles de clase**:

|**Type**|**Miembros que puede contener**|
|--------------| - |
|Clase|método, propiedad (para C# y Visual Basic), campo, evento (para C# y Visual Basic), constructor (método), destructor (método), constante|
|Enum|miembro|
|Interfaz|método, propiedad, evento (para C# y Visual Basic)|
|Clase abstracta|método, propiedad (para C# y Visual Basic), campo, evento (para C# y Visual Basic), constructor (método), destructor (método), constante|
|Estructura (struct en C#)|método, propiedad (para C# y Visual Basic), campo, evento (para C# y Visual Basic), constructor (método), constante|
|delegado|parámetro|
|Módulo (solo en VB)|método, propiedad, campo, evento, constructor, constante|

> [!NOTE]
> Haga que la declaración de la propiedad sea más concisa cuando no se requiere ninguna lógica adicional en los descriptores de acceso get y set de una propiedad usando las propiedades implementadas automáticamente (solo C#). Para mostrar la firma completa, en el menú **Diagrama de clase**, elija **Cambiar formato de los miembros** > **Mostrar firma completa**. Para obtener más información sobre las propiedades autoimplementadas, vea [Propiedades autoimplementadas](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido adicional|
|----------| - |
|**Primer paso:** antes de crear y configurar los miembros de tipo, debe abrir la ventana **Detalles de clase**.|- [Abrir la ventana Detalles de clase](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Notas de uso de Detalles de clase](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Presentación de la información de solo lectura](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Métodos abreviados de teclado y de mouse en el Diagrama de clases y la ventana Detalles de clase](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Crear y modificar miembros de tipo:** puede crear nuevos miembros, modificar miembros y agregar parámetros a un método mediante la ventana **Detalles de clase**.|- [Crear miembros](creating-and-configuring-type-members.md#create-members)<br />- [Modificar miembros de tipo](creating-and-configuring-type-members.md#modify-type-members)<br />- [Agregar parámetros a métodos](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Abrir la ventana Detalles de clase

De manera predeterminada, la ventana **Detalles de clase** aparece automáticamente cuando se abre un nuevo diagrama de clases. Vea [Cómo: Agregar diagramas de clases a proyectos](how-to-add-class-diagrams-to-projects.md)). También puede abrir la ventana **Detalles de clase** de las maneras siguientes:

- Haga clic con el botón derecho en cualquier clase del diagrama para que aparezca un menú contextual y después seleccione **Detalles de clase**.

- Seleccione **Ver** > **Otras ventanas** > **Detalles de clase** en la barra de menús.

## <a name="create-members"></a>Crear miembros

Puede crear un miembro con cualquiera de las herramientas siguientes:

- **Diseñador de clases**

- Barra de herramientas de la ventana **Detalles de clase**

- Ventana **Detalles de clase**

> [!NOTE]
> Los procedimientos de esta sección también permiten crear constructores y destructores. Tenga presente que los constructores y destructores son tipos especiales de métodos y, como tales, aparecen en el compartimiento **Métodos** de las formas del diagrama de clases y en la sección **Métodos** de la cuadrícula de la ventana **Detalles de clase**.

> [!NOTE]
> La única entidad que puede agregar a un delegado es un parámetro. Tenga en cuenta que el procedimiento titulado "Para crear un miembro con la barra de herramientas de la ventana **Detalles de clase**" no es válido para esta operación.

### <a name="create-a-member-using-class-designer"></a>Crear un miembro con el Diseñador de clases

1. Haga clic con el botón derecho en el tipo al que quiere agregar un miembro, pulse **Agregar** y, después, seleccione el tipo de miembro que quiere agregar.

     Se crea una nueva firma de miembro y se agrega al tipo. Se le asigna un nombre predeterminado que puede cambiar en el **Diseñador de clases**, la ventana **Detalles de clase** o la ventana **Propiedades**.

2. Si lo desea, puede especificar de forma opcional otros detalles sobre el miembro, como su tipo.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Crear un miembro con la barra de herramientas de la ventana Detalles de clase

1. En la superficie de diagrama, seleccione el tipo al que desee agregar un miembro.

     El tipo obtiene el foco y su contenido se muestra en la ventana **Detalles de clase**.

2. En la barra de herramientas de la ventana **Detalles de clase**, haga clic en el icono superior y seleccione **Nuevo \<miembro>** en la lista desplegable.

     El cursor se moverá al campo **Nombre** de una fila del tipo de miembro que quiere agregar. Por ejemplo, si ha hecho clic en **Nueva propiedad**, el cursor se mueve a una nueva fila de la sección **Propiedades** de la ventana **Detalles de clase**.

3. Escriba el nombre del miembro que desee crear y presione ENTRAR (o mueva el foco de otra forma, por ejemplo, presionando Tabulador).

     Se crea una nueva firma de miembro y se agrega al tipo. El miembro existe ahora en el código y aparece en el **Diseñador de clases**, la ventana **Detalles de clase** y la ventana Propiedades.

4. Si lo desea, puede especificar de forma opcional otros detalles sobre el miembro, como su tipo.

### <a name="create-a-member-using-the-class-details-window"></a>Crear un miembro con la ventana Detalles de clase

1. En la superficie de diagrama, seleccione el tipo al que desee agregar un miembro.

     El tipo obtiene el foco y su contenido se muestra en la ventana **Detalles de clase**.

2. En la ventana **Detalles de clase**, en la sección que contiene el tipo de miembro que quiere agregar, haga clic en **\<agregar miembro>** . Por ejemplo, si quiere agregar un campo, haga clic en **\<agregar campo>** .

3. Escriba el nombre del miembro que desee crear y presione ENTRAR.

     Se crea una nueva firma de miembro y se agrega al tipo. El miembro existe ahora en el código y aparece en el **Diseñador de clases**, la ventana **Detalles de clase** y la ventana Propiedades.

4. Si lo desea, puede especificar de forma opcional otros detalles sobre el miembro, como su tipo.

    > [!NOTE]
    > También puede usar métodos abreviados de teclado para crear miembros. Para obtener más información, vea [Métodos abreviados de teclado y de mouse en el diagrama de clases y la ventana de detalles de clase](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modificar miembros de tipo

El Diseñador de clases permite modificar los miembros de los tipos que aparecen en el diagrama. Puede modificar los miembros de cualquier tipo que aparezca en un diagrama de clases que no sean de solo lectura. Para modificar miembros de tipo, se usa la edición en contexto en la superficie de diseño, la ventana Propiedades y la ventana **Detalles de clase**.

Todos los miembros mostrados en la ventana **Detalles de clase** representan los miembros de los tipos del diagrama de clases. Hay cuatro tipos de miembros: métodos, propiedades, campos y eventos.

Todas las filas de miembro aparecen bajo encabezados que agrupan los miembros por tipo. Por ejemplo, todas las propiedades aparecen bajo el encabezado **Propiedades** que, al igual que los nodos de la cuadrícula, se puede contraer o expandir.

Cada fila de miembro muestra los elementos siguientes:

- **Icono de miembro**

     Cada tipo de miembro está representado por su propio icono. Señale con el mouse el icono del miembro para mostrar su firma. Haga clic en el icono del miembro o en el espacio en blanco situado a su izquierda para seleccionar la fila.

- **Nombre de miembro**

     La columna **Nombre** de una fila muestra el nombre del miembro. Este nombre también se muestra en la propiedad **Nombre** de la ventana Propiedades. Use esta celda para cambiar el nombre de cualquier miembro que tenga permisos de lectura y escritura.

     Si la columna **Nombre** es demasiado estrecha como para mostrar el nombre completo, puede señalarlo con el mouse para que se muestre por completo.

- **Tipo de miembro**

     La celda **Tipo de miembro** usa IntelliSense, lo que permite seleccionar un elemento en una lista con todos los tipos disponibles en el proyecto actual y en los proyectos a los que se hace referencia.

- **Modificador de miembro**

     Cambie el modificador de visibilidad de un miembro a `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected Friend` (`protected internal`) o `Default`.

- **\<agregar miembro>**

     La última fila de la ventana **Detalles de clase** contiene el texto **\<agregar miembro>** en la celda **Nombre**. Puede crear un nuevo miembro haciendo clic en esta celda. Para obtener más información, vea [Crear miembros](creating-and-configuring-type-members.md#create-members).

- **Propiedades de miembro en la ventana Propiedades**

     La ventana **Detalles de clase** muestra un subconjunto de las propiedades del miembro que se muestran en la ventana Propiedades. Al cambiar una propiedad en una ubicación, el valor de la propiedad se actualizará globalmente. Esta actualización incluye la presentación de su valor en la otra ubicación.

- **Resumen**

     La celda **Resumen** muestra un resumen de la información sobre el miembro. Haga clic en los puntos suspensivos de la celda **Resumen** para ver o editar la información de **Resumen**, **Tipo de valor devuelto** y **Comentarios** del miembro.

- **Ocultar**

     Cuando la casilla **Ocultar** está activada, el miembro no se muestra en el tipo.

### <a name="to-modify-a-type-member"></a>Para modificar un miembro de tipo

1. Con el Diseñador de clases, seleccione un tipo.

2. Si no aparece la ventana **Detalles de clase**, haga clic en el botón **Ventana Detalles de clase** de la barra de herramientas del Diseñador de clases.

3. Edite los valores de los campos de la cuadrícula de la ventana **Detalles de clase**. Después de cada modificación, presione ENTRAR o aleje el foco del campo editado, presionando, por ejemplo, la tecla TAB. Los cambios se reflejan de inmediato en el código.

    > [!NOTE]
    > Si desea modificar únicamente el nombre de un miembro, puede hacerlo mediante la edición en contexto.

## <a name="add-parameters-to-methods"></a>Agregar parámetros a métodos

Agregue parámetros a métodos mediante la ventana **Detalles de clase**. Los parámetros se pueden configurar como necesarios u opcionales. Al proporcionar un valor para la propiedad **predeterminada opcional** de un parámetro, se indica al diseñador que genere código como parámetro opcional.

Las filas de parámetros contienen los elementos siguientes:

- **Name**

     La columna **Nombre** de una fila del parámetro muestra el nombre del parámetro. Este nombre también se muestra en la propiedad **Nombre** de la ventana Propiedades. Puede utilizar esta celda para cambiar el nombre de cualquier parámetro con permisos de lectura y escritura.

     Si la columna **Nombre** es demasiado estrecha para mostrar el nombre completo del parámetro, señale el nombre para que este aparezca en la pantalla.

- **Type**

     En la celda **Tipo de parámetro** se usa IntelliSense, lo que permite elegir de una lista de todos los tipos disponibles en el proyecto actual o en los proyectos a los que se hace referencia.

- **Modificador**

     La celda **Modificador** de una fila de parámetro acepta y muestra el nuevo modificador del parámetro. Para escribir un nuevo modificador de parámetro, use el cuadro de lista desplegable para seleccionar entre **None**, **ref**, **out** o **params** en C# y **ByVal**, **ByRef** o **ParamArray** en VB.

- **Resumen**

     La celda **Resumen** de una fila de parámetro permite escribir comentarios de código que aparecen en IntelliSense al registrar el parámetro en el editor de código.

- **\<agregar parámetro>**

     La última fila de parámetros de un miembro contiene el texto **<agregar parámetro\>** en la celda **Nombre**. Haga clic en esta celda para crear un nuevo parámetro. Para obtener más información, vea [Para agregar un parámetro a un método](creating-and-configuring-type-members.md#add-parameters-to-methods).

La ventana **Propiedades** muestra las mismas propiedades de parámetro que la ventana **Detalles de clase**: **Nombre**, **Tipo**, **Modificador** y **Resumen**, así como la propiedad **Valor predeterminado opcional**. Al cambiar una propiedad en una ubicación, se actualiza globalmente el valor de la propiedad, incluida la presentación de su valor en la otra ubicación.

> [!NOTE]
> Para agregar un parámetro a un delegado, vea [Crear miembros](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> A pesar de ser un método, un destructor no puede tener parámetros.

### <a name="to-add-a-parameter-to-a-method"></a>Para agregar un parámetro a un método

1. En la superficie de diagrama, haga clic en el tipo que contenga el método al que desee agregar un parámetro.

     El tipo obtiene el foco y su contenido se muestra en la ventana **Detalles de clase**.

2. En la ventana **Detalles de clase**, expanda la fila del método al que quiere agregar un parámetro.

     Aparece una fila de parámetro con sangría que solo contiene el siguiente texto entre paréntesis **\<agregar parámetro>** .

3. Haga clic en **\<agregar parámetro>** , escriba el nombre del nuevo parámetro y presione **Entrar**.

     El nuevo parámetro se agrega al método y al código de este. Aparece en las ventanas **Detalles de clase** y Propiedades.

4. De forma opcional, puede especificar otros detalles sobre el parámetro, como el tipo.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Para agregar un parámetro opcional a un método

1. En la superficie del diagrama, haga clic en el tipo que contenga el método al que desee agregar un parámetro opcional.

     El tipo obtiene el foco y su contenido se muestra en la ventana **Detalles de clase**.

2. En la ventana **Detalles de clase**, expanda la fila del método al que quiere agregar un parámetro opcional.

     Aparece una fila de parámetro con sangría que solo contiene el siguiente texto entre paréntesis **\<agregar parámetro>** .

3. Haga clic en **\<agregar parámetro>** , escriba el nombre del nuevo parámetro y presione **Entrar**.

     El nuevo parámetro se agrega al método y al código de este. Aparece en las ventanas **Detalles de clase** y Propiedades.

4. En la ventana Propiedades, escriba un valor para la propiedad **predeterminada opcional**. Al establecer la propiedad predeterminada opcional de un parámetro, ese parámetro pasa a ser opcional.

    > [!NOTE]
    > Los parámetros opcionales deben ser los últimos parámetros en la lista de parámetros.

## <a name="class-details-usage-notes"></a>Notas de uso de Detalles de clase

Tenga en cuenta las siguientes sugerencias cuando use la ventana **Detalles de clase**.

### <a name="editable-and-non-editable-cells"></a>Celdas modificables y no modificables

Todas las celdas de la ventana **Detalles de clase** son modificables, con unas pocas excepciones:

- Todo el tipo es de solo lectura cuando, por ejemplo, se encuentra en un ensamblado al que se hace referencia. Cuando se selecciona la forma en el Diseñador de clases, la ventana **Detalles de clase** muestra los detalles en estado de solo lectura.

- En el caso de los indizadores, el nombre es de sólo lectura y el resto de los datos (tipo, modificador, resumen) son modificables.

- En la ventana **Detalles de clase**, los parámetros de todos los genéricos son de solo lectura. Para cambiar un parámetro genérico, edite su código fuente.

- El nombre del parámetro de tipo definido en un tipo genérico es de sólo lectura.

- Cuando el código de un tipo está dañado (no es analizable), la ventana **Detalles de clase** muestra el contenido del tipo como de solo lectura.

### <a name="the-class-details-window-and-source-code"></a>Ventana Detalles de clase y código fuente

- Para ver el código fuente, puede hacer clic con el botón derecho en una forma de la ventana **Detalles de clase** (o del Diseñador de clases) y luego hacer clic en Ver código. El archivo de código fuente se abre y se desplaza hasta el elemento seleccionado.

- Los cambios realizados en el código fuente se reflejan inmediatamente en la presentación de información de firma en el Diseñador de clases y en la ventana **Detalles de clase**. Si la ventana **Detalles de clase** está cerrada, la nueva información puede verse cuando se vuelve a abrir.

- Cuando el código de un tipo está dañado (no es analizable), la ventana **Detalles de clase** muestra el contenido del tipo como de solo lectura.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funcionalidad del Portapapeles en la ventana Detalles de clase

Puede copiar o cortar campos o filas de la ventana **Detalles de clase** y pegarlos en otro tipo. Sólo puede cortar una fila si no es de sólo lectura. Cuando se pega la fila, la ventana **Detalles de clase** le asigna un nuevo nombre (derivado del nombre de la fila copiada) para evitar un conflicto.

## <a name="display-of-read-only-information"></a>Presentación de la información de solo lectura

El Diseñador de clases y la ventana **Detalles de clase** pueden mostrar los tipos (y los miembros de tipos) de:

- un proyecto que contiene un diagrama de clases

- un proyecto al que se hace referencia desde un proyecto que contiene un diagrama de clases

- un ensamblado al que se hace referencia desde un proyecto que contiene un diagrama de clases

En los dos últimos casos, la entidad a la que se hace referencia (un tipo o miembro) es de solo lectura en el diagrama de clases que la representa.

Un proyecto completo o determinadas partes de él, como archivos individuales, pueden ser de sólo lectura. Los casos más comunes en los que un proyecto o uno de sus archivos es de sólo lectura se dan cuando está bajo control de código fuente (y no desprotegido), cuando existe en un ensamblado externo o cuando el sistema operativo considera que los archivos son de sólo lectura.

**Control de código fuente**

Dado que un diagrama de clases se guarda como un archivo en un proyecto, es necesario extraer del repositorio el proyecto para guardar cualquier cambio realizado en el Diseñador de clases o en la ventana **Detalles de clase**.

**Proyectos de solo lectura**

El proyecto puede ser de sólo lectura por razones distintas del control de código fuente. Cuando se cierra el proyecto, aparece un cuadro de diálogo que pregunta si se quiere sobrescribir el archivo de proyecto, descartar los cambios (no guardar) o cancelar la operación de cierre. Si elige sobrescribir, los archivos de proyecto se sobrescriben y pasan a ser de lectura y escritura. Se agrega el nuevo archivo de diagrama de clases.

**Tipos de solo lectura**

Si intenta guardar un proyecto que contiene un tipo cuyo archivo de código fuente es de solo lectura, aparece el cuadro de diálogo **Guardar el archivo de solo lectura**, en él podrá elegir si quiere guardar el archivo con otro nombre o en otra ubicación, o si quiere sobrescribir el archivo de solo lectura. Si sobrescribe el archivo, la nueva copia no será de sólo lectura.

Si un archivo de código contiene un error de sintaxis, las formas que muestran código de dicho archivo serán de sólo lectura hasta que se corrija el error de sintaxis. Mientras permanecen en este estado, las formas presentan el texto en color rojo, y aparece un icono rojo con la siguiente información sobre herramientas: "El archivo de código fuente contiene un error de análisis".

Los tipos a los que se hace referencia (como uno de .NET), que existen bajo el nodo de otro proyecto o bajo un nodo de ensamblado al que se hace referencia, aparecen indicados en la superficie de diseño del Diseñador de clases como de solo lectura. Los tipos locales, que existen en el proyecto abierto, son de lectura y escritura, y así lo indica la forma correspondiente en la superficie de diseño del Diseñador de clases.

Los indizadores son de lectura y escritura en el código y en la ventana **Detalles de clase**, pero el nombre del indizador es de solo lectura.

No es posible modificar métodos parciales mediante el Diseñador de clases o la ventana **Detalles de clase**; debe usar el Editor de código para hacerlo.

No puede modificar código C++ nativo mediante el Diseñador de clases o la ventana **Detalles de clase**; debe usar el Editor de código para hacerlo.

## <a name="see-also"></a>Vea también

- [Visualización de tipos y relaciones](designing-and-viewing-classes-and-types.md)
- [Refactorización de clases y tipos](refactoring-classes-and-types.md)
