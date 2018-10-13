---
title: Agregar iconos a comandos de menú | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b264a6b03baf5b77796b329ef6dd05fa4614bad0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184527"
---
# <a name="adding-icons-to-menu-commands"></a>Adición de iconos a comandos de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los comandos pueden aparecer en los menús y barras de herramientas. En las barras de herramientas, es común para un comando que se mostrará con un icono (para ahorrar espacio) mientras en los menús aparece normalmente en un comando con un icono y el texto.  
  
 Los iconos son 16 píxeles de ancho por 16 píxeles de alto y pueden ser la profundidad de color de 8 bits (256 colores) o la profundidad de color de 32 bits (color verdadero). se prefieren los iconos de color de 32 bits. Iconos normalmente están organizados en una sola fila horizontal en un único mapa de bits, aunque se permiten varios mapas de bits. Este mapa de bits se declara en el archivo .vsct, junto con los iconos individuales disponibles en el mapa de bits. Consulte la referencia para la [Bitmaps (elemento)](../extensibility/bitmaps-element.md) para obtener más detalles.  
  
## <a name="adding-an-icon-to-a-command"></a>Agregar un icono a un comando  
 El siguiente procedimiento se supone que tiene un proyecto de VSPackage existente con un comando de menú. Para averiguar cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Cree un mapa de bits con una profundidad de color de 32 bits. Siempre es un icono de 16 x 16 para que este mapa de bits debe ser de 16 píxeles de alto y un múltiplo de 16 píxeles de ancho.  
  
     Cada icono se coloca en el mapa de bits juntos en una sola fila. Use el canal alfa para indicar los lugares de transparencia en cada icono.  
  
     Si usa una profundidad de color de 8 bits, utilice magenta, `RGB(255,0,255)`, como la transparencia. Sin embargo, los iconos de color de 32 bits se prefieren.  
  
2.  Copie el archivo de icono en el directorio de recursos en el proyecto de VSPackage. En el Explorador de soluciones, agregue el icono al proyecto. (Seleccionar recursos y en el menú contextual, haga clic en Agregar y, a continuación, elemento existente y seleccione el archivo de icono).  
  
3.  Abra el archivo .vsct en el editor.  
  
4.  Agregar un `GuidSymbol` elemento con un nombre de **testIcon**. Crear un GUID (**herramientas / crear GUID**, a continuación, seleccione **formato del registro** y haga clic en Copiar) y péguelo en el `value` atributo. El resultado debería tener este aspecto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Agregar un `<IDSymbol>` para el icono. El `name` atributo es el identificador del icono y el `value` indica su posición en la banda, si existe. Si hay un solo icono, agregue 1. El resultado debería tener este aspecto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Crear un `<Bitmap>` en la `<Bitmaps>` sección del archivo .vsct para representar el mapa de bits que contiene los iconos.  
  
    -   Establecer el `guid` valor el nombre de la `<GuidSymbol>` que creó en el paso anterior del elemento.  
  
    -   Establecer el `href` valor a la ruta de acceso relativa del archivo de mapa de bits (en este caso **recursos\\< nombre de archivo de icono\>**.  
  
    -   Establecer el `usedList` valor para el IDSymbol que creó anteriormente. Este atributo especifica una lista delimitada por comas de los iconos que se usará en el VSPackage. Los iconos no están en la lista son compilación excluidos del formulario.  
  
         El bloque de mapa de bits debe tener este aspecto:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Existente `<Button>` elemento, establezca el `Icon` elemento con los valores de GUIDSymbol y IDSymbol que creó anteriormente. Este es un ejemplo de un elemento Button con esos valores:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  El icono de prueba. Compile la solución y comience la depuración. En la instancia experimental, busque el comando. Debería ver el icono que agregó.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)

