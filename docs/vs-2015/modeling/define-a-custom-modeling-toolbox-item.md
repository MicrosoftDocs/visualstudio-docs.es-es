---
title: Define a custom modeling toolbox item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299287"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definir un elemento personalizado en un cuadro de herramientas de modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para que le resulte más fácil crear un elemento o grupo de elementos conforme a un patrón que use habitualmente, puede agregar nuevas herramientas al cuadro de herramientas de los diagramas de modelado de Visual Studio. Puede distribuir estos elementos del cuadro de herramientas a otros usuarios de Visual Studio.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Una herramienta personalizada crea uno o varios elementos en un diagrama. Por ejemplo, puede crear una herramienta personalizada para elaborar elementos como los siguientes:

- Un paquete vinculado al perfil de .NET y una clase con el estereotipo de .NET.

- Un par de clases vinculadas mediante una asociación para representar el patrón Observer.

> [!NOTE]
> Puede usar este método para crear herramientas de elemento. Es decir, puede crear herramientas que se arrastren desde el cuadro de herramientas a un diagrama. No se pueden crear herramientas de conector.

## <a name="DefineTool"></a> Defining a Custom Modeling Tool

#### <a name="to-define-a-custom-modeling-tool"></a>Para definir una herramienta de modelado personalizada

1. Crear un diagrama UML que contenga un elemento o grupo de elementos.

    - Estos elementos pueden tener relaciones entre ellos y pueden tener elementos secundarios como puertos, atributos, operaciones o pins.

2. Guarde el diagrama con el nombre que desea asignar a la nueva herramienta. On the **File** menu, use **Save…As**.

3. En el Explorador de Windows, copie los dos archivos de diagrama en la siguiente carpeta o en cualquier subcarpeta:

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom Toolbox Items**

    - Cree esta carpeta si no existe ya. You might have to create both **Architecture Tools** and **Custom Toolbox Items**.

    - Copy both diagram files, one with a name that ends "…**diagram**" and the other with a name that ends "…**diagram.layout**"

    - Puede crear tantas herramientas personalizadas como desee. Use un diagrama para cada herramienta.

4. (Optional) Create a **.tbxinfo** file as described in [How to Define the Properties of Custom Tools](#tbxinfo), and add it to the same directory. De este modo, podrá definir un icono de cuadro de herramientas, información sobre herramientas, etcétera.

    - A single **.tbxinfo** file can be used to define several tools. Este archivo puede hacer referencia a los archivos de diagrama que se encuentran en las subcarpetas.

5. Reinicie Visual Studio. La herramienta adicional aparecerá en el cuadro de herramientas para el tipo de diagrama adecuado.

### <a name="what-the-custom-tool-will-replicate"></a>Qué va a replicar la herramienta personalizada
 Una herramienta personalizada replicará la mayoría de las características del diagrama de origen:

- Nombres. Cuando se crea un elemento a partir del cuadro de herramientas, se agrega un número al final del nombre si es necesario para evitar que se dupliquen los nombres en el mismo espacio de nombres.

- Colores, tamaños y formas.

- Perfiles de estereotipos y paquetes.

- Valores de propiedad, como Is Abstract.

- Elementos de trabajo vinculados.

- Multiplicidades y otras propiedades de las relaciones.

- Posiciones relativas de las formas.

  Estas características no se conservarán en una herramienta personalizada:

- Formas simples. Son formas que no están relacionadas con elementos del modelo y se pueden dibujar en algunos tipos de diagramas.

- Enrutamiento de conectores. Si se enrutan conectores manualmente, el enrutamiento no se conservará cuando se use la herramienta. Las posiciones de algunas formas anidadas, como los puertos, no se conservan con relación a sus propietarios.

## <a name="tbxinfo"></a> How to Define the Properties of Custom Tools
 A toolbox information ( **.tbxinfo**) file allows you to specify a toolbox name, icon, tooltip, tab, and help keyword for one or more custom tools. Give it any name, such as **MyTools.tbxinfo**.

 El formato general del archivo es como este:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 El valor de cada elemento puede ser:

- Como puede ver en el ejemplo, `<bmp fileName="…"/>` para el icono de cuadro de herramientas y `<value>string</value>` para los demás elementos.

  \- o -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   En este caso, debe proporcionar un ensamblado compilado en el que los valores de cadena se hayan compilado como recursos.

  Agregue un nodo `<customToolboxItem>` para cada elemento del cuadro de herramientas que quiera definir.

  The nodes in the **.tbxinfo** file are as follows. Hay un valor predeterminado para cada nodo.

|Nombre del nodo|Qué define|
|---------------|-------------|
|displayName|El nombre del elemento del cuadro de herramientas.|
|tabName|La pestaña del cuadro de herramientas en la que debe aparecer el elemento. Puede especificar el nombre de la pestaña habitual para este tipo de diagrama o un nombre distinto.|
|imagen|The location of the bitmap ( **.bmp**) file, which must have height and width of 16, and a color depth of 24 bits.|
|f1Keyword|La palabra clave que localiza un tema de ayuda.|
|información sobre herramientas|Información sobre esta herramienta.|

 Puede editar el archivo de mapa de bits en Visual Studio y establecer el alto y ancho en 16 en la ventana Propiedades.

> [!NOTE]
> Si empieza a usar un archivo .tbxinfo después de experimentar con archivos de diagrama en solitario, es posible que el cuadro de herramientas contenga la versión anterior y la versión nueva de un cuadro de herramientas. Esto también puede producirse si el nombre del archivo de diagrama se escribió incorrectamente en el archivo .tbxinfo. If this occurs, on the shortcut menu of the toolbox choose **Reset Toolbox**. Los elementos de cuadro de herramientas personalizados desaparecerán. Reinicie Visual Studio y aparecerán los elementos personalizados correctos.

## <a name="Extension"></a> How to Distribute Toolbox Items in a Visual Studio Extension
 You can distribute toolbox items to other [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] users by packaging them into a Visual Studio Extension (VSIX). Puede empaquetar comandos, perfiles y otras extensiones en el mismo archivo VSIX. For more information, see [Deploying Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160780).

 La manera habitual de compilar una extensión de Visual Studio es usar la plantilla de proyecto de VSIX. Para ello, debe tener instalado [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Para agregar un elemento del cuadro de herramientas a una extensión de Visual Studio

1. [Create and test one or more custom tools](#DefineTool).

2. [Create a .tbxinfo file](#tbxinfo) that references the tools.

3. Abra un proyecto de extensión de Visual Studio que ya esté creado.

     \- o -

     Defina un nuevo proyecto de extensión de Visual Studio.

    1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

    2. In the **New Project** dialog box, under **Installed Templates**, choose **Visual C#** , **Extensibility**, **VSIX project**.

4. Agregue las definiciones del cuadro de herramientas al proyecto. Include the **.tbxinfo** file, the diagram files, bitmap files, and any resource files, and make sure that they are included in the VSIX.

    - In Solution Explorer, on the shortcut menu of the VSIX project, choose **Add**, **Existing Item**. In the dialog box, set **Objects of Type: All Files**. Locate the files, select them all, and then choose **Add**.

        > [!NOTE]
        > En este proyecto, los archivos de diagrama no se pueden abrir en el editor de modelos.

5. Establezca las siguientes propiedades de todos los archivos que acaba de agregar. Puede establecer sus propiedades al mismo tiempo si los selecciona todos en el Explorador de soluciones. Tenga cuidado de no cambiar las propiedades de los demás archivos del proyecto.

     **Copy to Output Directory** = **Copy Always**

     **Build Action** = **Content**

     **Include in VSIX** = **true**

6. Abra **source.extension.vsixmanifest**. El archivo se abre en el editor de manifiestos de la extensión.

7. Under **Metadata**, add a description for the custom tools.

     Under **Assets**, choose **New** and then set the fields in the dialog as follows:

    - **Type** = **Custom Extension Type**

    - Tipo = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Esta no es una de las opciones de la lista desplegable. Debe escribirla mediante el teclado.

    - **Source** = **File on filesystem**.

    - **Path** = your **.tbxinfo** file, for example **MyTools.tbxinfo**

8. Compile el proyecto.

9. **To verify that the extension works**, press F5. Se abre la instancia experimental de Visual Studio.

     En la instancia experimental, cree o abra un diagrama de UML del tipo pertinente. Compruebe que la nueva herramienta aparece en el cuadro de herramientas y que crea elementos correctamente.

10. **To obtain a VSIX file for deployment:** In Windows Explorer, open the folder **.\bin\Debug** or **.\bin\Release** to find the **.vsix** file. Es un archivo de la extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Puede instalarse en el equipo y también enviarse a otros usuarios de Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Para instalar herramientas personalizadas desde una extensión de Visual Studio

1. Abra el archivo `.vsix` en el Explorador de Windows o en Visual Studio.

2. Choose **Install** in the dialog box that appears.

3. To uninstall or temporarily disable the extension, open **Extensions and Updates** from the **Tools** menu.

## <a name="localization"></a>Localización
 Puede crear una extensión que, cuando se instale en otro equipo, muestre los nombres de herramientas y la información sobre herramientas en el idioma del equipo de destino.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Para proporcionar versiones de la herramienta en varios idiomas

1. Cree un proyecto de extensión de Visual Studio que contenga una o varias herramientas personalizadas.

    In the **.tbxinfo** file, use the resource file method to define the tool's `displayName`, toolbox `tabName`, and the tooltip. Cree un archivo de recursos en el que se definan estas cadenas, compílelo en un ensamblado y establezca referencias a él en el archivo tbxinfo.

2. Cree ensamblados adicionales que contengan archivos de recursos con cadenas en otros idiomas.

3. Coloque cada ensamblado adicional en una carpeta cuyo nombre sea el código de referencia cultural del idioma. For example, place a French version of the assembly inside a folder that is named **fr**.

4. Debe utilizar un código de referencia cultural neutro, normalmente dos letras, y no una referencia cultural concreta como `fr-CA`. For more information about culture codes, see [CultureInfo.GetCultures method](https://go.microsoft.com/fwlink/?LinkId=160782), which provides a complete list of culture codes.

5. Compile la extensión de Visual Studio y distribúyala.

6. Cuando la extensión se instala en otro equipo, se carga automáticamente la versión del archivo de recursos correspondiente a la referencia cultural local del usuario. Si no se proporciona ninguna versión para la referencia cultural del usuario, se usarán los recursos predeterminados.

   No puede usar este método para instalar versiones diferentes del diagrama de prototipos. Los nombres de los elementos y conectores serán los mismos en todas las instalaciones.

## <a name="other-toolbox-operations"></a>Otras operaciones del cuadro de herramientas
 Normalmente, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] permite personalizar el cuadro de herramientas: puede cambiar el nombre de las herramientas, moverlas a diferentes pestañas del cuadro de herramientas y eliminarlas. Pero estos cambios no se mantienen en las herramientas de modelado personalizadas que se crean mediante los procedimientos descritos en este tema. Cuando se reinicia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], las herramientas personalizadas volverán a aparecer con sus nombres definidos y las ubicaciones del cuadro de herramientas.

 Furthermore, your custom tools will disappear if you perform the **Reset Toolbox** command. Sin embargo, volverán a aparecer cuando reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Vea también
 [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)
