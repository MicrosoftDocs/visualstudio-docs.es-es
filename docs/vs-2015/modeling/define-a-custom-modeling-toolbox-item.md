---
title: Definir un elemento personalizado del cuadro de herramientas de modelado | Microsoft Docs
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
ms.openlocfilehash: 27692c31c2c0f1c52ab026fb2d55e5d240839ff3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654903"
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

## <a name="DefineTool"></a>Definir una herramienta de modelado personalizada

#### <a name="to-define-a-custom-modeling-tool"></a>Para definir una herramienta de modelado personalizada

1. Crear un diagrama UML que contenga un elemento o grupo de elementos.

    - Estos elementos pueden tener relaciones entre ellos y pueden tener elementos secundarios como puertos, atributos, operaciones o pins.

2. Guarde el diagrama con el nombre que desea asignar a la nueva herramienta. En el menú **archivo** , use **Guardar... Como**.

3. En el Explorador de Windows, copie los dos archivos de diagrama en la siguiente carpeta o en cualquier subcarpeta:

     **Elementos del cuadro de herramientas YourDocuments \Visual Studio\Architecture Tools\Custom**

    - Cree esta carpeta si no existe ya. Es posible que tenga que crear tanto **herramientas de arquitectura** como **elementos personalizados del cuadro de herramientas**.

    - Copie ambos archivos de diagrama, uno con un nombre que termine "... **Diagrama**"y el otro con un nombre que termina"... **diagram. layout**"

    - Puede crear tantas herramientas personalizadas como desee. Use un diagrama para cada herramienta.

4. Opta Cree un archivo **. archivo tbxinfo** como se describe en [cómo definir las propiedades de herramientas personalizadas](#tbxinfo)y agréguelo al mismo directorio. De este modo, podrá definir un icono de cuadro de herramientas, información sobre herramientas, etcétera.

    - Se puede usar un único archivo **. archivo tbxinfo** para definir varias herramientas. Este archivo puede hacer referencia a los archivos de diagrama que se encuentran en las subcarpetas.

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

## <a name="tbxinfo"></a>Cómo definir las propiedades de herramientas personalizadas
 Un archivo de información del cuadro de herramientas ( **. archivo tbxinfo**) permite especificar un nombre de cuadro de herramientas, un icono, una información sobre herramientas, una pestaña y una palabra clave de ayuda para una o varias herramientas personalizadas. Asígnele cualquier nombre, como, por ejemplo, **archivo tbxinfo**.

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

  Los nodos del archivo **. archivo tbxinfo** son los siguientes. Hay un valor predeterminado para cada nodo.

|Nombre del nodo|Qué define|
|---------------|-------------|
|displayName|El nombre del elemento del cuadro de herramientas.|
|tabName|La pestaña del cuadro de herramientas en la que debe aparecer el elemento. Puede especificar el nombre de la pestaña habitual para este tipo de diagrama o un nombre distinto.|
|imagen|Ubicación del archivo de mapa de bits ( **. bmp**), que debe tener el alto y el ancho de 16, y una profundidad de color de 24 bits.|
|f1Keyword|La palabra clave que localiza un tema de ayuda.|
|información sobre herramientas|Información sobre esta herramienta.|

 Puede editar el archivo de mapa de bits en Visual Studio y establecer el alto y ancho en 16 en la ventana Propiedades.

> [!NOTE]
> Si empieza a usar un archivo .tbxinfo después de experimentar con archivos de diagrama en solitario, es posible que el cuadro de herramientas contenga la versión anterior y la versión nueva de un cuadro de herramientas. Esto también puede producirse si el nombre del archivo de diagrama se escribió incorrectamente en el archivo .tbxinfo. Si esto ocurre, en el menú contextual del cuadro de herramientas, elija **restablecer cuadro de herramientas**. Los elementos de cuadro de herramientas personalizados desaparecerán. Reinicie Visual Studio y aparecerán los elementos personalizados correctos.

## <a name="Extension"></a>Cómo distribuir elementos del cuadro de herramientas en una extensión de Visual Studio
 Puede distribuir los elementos del cuadro de herramientas a otros usuarios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] si los empaqueta en una extensión de Visual Studio (VSIX). Puede empaquetar comandos, perfiles y otras extensiones en el mismo archivo VSIX. Para obtener más información, consulte [implementación de extensiones de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).

 La manera habitual de compilar una extensión de Visual Studio es usar la plantilla de proyecto de VSIX. Para ello, debe tener instalado [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Para agregar un elemento del cuadro de herramientas a una extensión de Visual Studio

1. [Cree y pruebe una o varias herramientas personalizadas](#DefineTool).

2. [Cree un archivo. archivo tbxinfo](#tbxinfo) que haga referencia a las herramientas de.

3. Abra un proyecto de extensión de Visual Studio que ya esté creado.

     \- o -

     Defina un nuevo proyecto de extensión de Visual Studio.

    1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

    2. En el cuadro de diálogo **nuevo proyecto** , en **plantillas instaladas**, elija **Visual C#** , **extensibilidad**, **Proyecto VSIX**.

4. Agregue las definiciones del cuadro de herramientas al proyecto. Incluya el archivo **. archivo tbxinfo** , los archivos de diagrama, los archivos de mapa de bits y cualquier archivo de recursos, y asegúrese de que están incluidos en el VSIX.

    - En Explorador de soluciones, en el menú contextual del Proyecto VSIX, elija **Agregar**, **elemento existente**. En el cuadro de diálogo, establezca **objetos de tipo: todos los archivos**. Busque los archivos, selecciónelos todos y, a continuación, elija **Agregar**.

        > [!NOTE]
        > En este proyecto, los archivos de diagrama no se pueden abrir en el editor de modelos.

5. Establezca las siguientes propiedades de todos los archivos que acaba de agregar. Puede establecer sus propiedades al mismo tiempo si los selecciona todos en el Explorador de soluciones. Tenga cuidado de no cambiar las propiedades de los demás archivos del proyecto.

     **Copiar en el directorio de salida**  = **copiar siempre**

     **Contenido** de la **acción de compilación**  = 

     **Incluir en VSIX**  = **true**

6. Abra **source.extension.vsixmanifest**. El archivo se abre en el editor de manifiestos de la extensión.

7. En **metadatos**, agregue una descripción para las herramientas personalizadas.

     En **recursos**, elija **nuevo** y, a continuación, establezca los campos del cuadro de diálogo de la siguiente manera:

    - **Escribir**  = **tipo de extensión personalizada**

    - Tipo = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Esta no es una de las opciones de la lista desplegable. Debe escribirla mediante el teclado.

    - **Archivo de  =  de origen en el sistema de archivos**.

    - **Path** = el archivo **. archivo tbxinfo** , por ejemplo, las **herramientas. archivo tbxinfo**

8. Compile el proyecto.

9. Presione F5 **para comprobar que la extensión funciona**. Se abre la instancia experimental de Visual Studio.

     En la instancia experimental, cree o abra un diagrama de UML del tipo pertinente. Compruebe que la nueva herramienta aparece en el cuadro de herramientas y que crea elementos correctamente.

10. **Para obtener un archivo VSIX para la implementación:** En el explorador de Windows, abra la carpeta **.\bin\Debug** o **.\bin\Release** para buscar el archivo **. vsix** . Es un archivo de la extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Puede instalarse en el equipo y también enviarse a otros usuarios de Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Para instalar herramientas personalizadas desde una extensión de Visual Studio

1. Abra el archivo `.vsix` en el Explorador de Windows o en Visual Studio.

2. Elija **instalar** en el cuadro de diálogo que aparece.

3. Para desinstalar o deshabilitar temporalmente la extensión, Abra **extensiones y actualizaciones** en el menú **herramientas** .

## <a name="localization"></a>Localización
 Puede crear una extensión que, cuando se instale en otro equipo, muestre los nombres de herramientas y la información sobre herramientas en el idioma del equipo de destino.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Para proporcionar versiones de la herramienta en varios idiomas

1. Cree un proyecto de extensión de Visual Studio que contenga una o varias herramientas personalizadas.

    En el archivo **. archivo tbxinfo** , use el método de archivo de recursos para definir el `displayName`, el cuadro de herramientas `tabName` de la herramienta y la información sobre herramientas. Cree un archivo de recursos en el que se definan estas cadenas, compílelo en un ensamblado y establezca referencias a él en el archivo tbxinfo.

2. Cree ensamblados adicionales que contengan archivos de recursos con cadenas en otros idiomas.

3. Coloque cada ensamblado adicional en una carpeta cuyo nombre sea el código de referencia cultural del idioma. Por ejemplo, coloque una versión en francés del ensamblado dentro de una carpeta denominada **fr**.

4. Debe utilizar un código de referencia cultural neutro, normalmente dos letras, y no una referencia cultural concreta como `fr-CA`. Para obtener más información sobre los códigos de referencia cultural, vea [método CultureInfo. GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), que proporciona una lista completa de códigos de referencia cultural.

5. Compile la extensión de Visual Studio y distribúyala.

6. Cuando la extensión se instala en otro equipo, se carga automáticamente la versión del archivo de recursos correspondiente a la referencia cultural local del usuario. Si no se proporciona ninguna versión para la referencia cultural del usuario, se usarán los recursos predeterminados.

   No puede usar este método para instalar versiones diferentes del diagrama de prototipos. Los nombres de los elementos y conectores serán los mismos en todas las instalaciones.

## <a name="other-toolbox-operations"></a>Otras operaciones del cuadro de herramientas
 Normalmente, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] permite personalizar el cuadro de herramientas: puede cambiar el nombre de las herramientas, moverlas a diferentes pestañas del cuadro de herramientas y eliminarlas. Pero estos cambios no se mantienen en las herramientas de modelado personalizadas que se crean mediante los procedimientos descritos en este tema. Cuando se reinicia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], las herramientas personalizadas volverán a aparecer con sus nombres definidos y las ubicaciones del cuadro de herramientas.

 Además, las herramientas personalizadas desaparecerán si realiza el comando **restablecer cuadro de herramientas** . Sin embargo, volverán a aparecer cuando reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Vea también
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md) [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)
