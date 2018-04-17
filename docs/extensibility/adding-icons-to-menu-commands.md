---
title: Agregar iconos a los comandos de menú | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8591c55a176493ace23df2de61ba26d58a3155e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="adding-icons-to-menu-commands"></a>Agregar iconos a los comandos de menú
Los comandos pueden aparecer en los menús y barras de herramientas. En las barras de herramientas, es común para un comando que se mostrará con solo un icono (para ahorrar espacio) mientras en los menús normalmente aparece un comando con un icono y el texto.  
  
 Iconos son 16 píxeles de ancho por 16 píxeles de alto y pueden ser la profundidad de color de 8 bits (256 colores) o la profundidad de color de 32 bits (color verdadero). se prefieren los iconos de colores de 32 bits. Normalmente se organizan los iconos en una sola fila horizontal en un mapa de bits único, aunque se permiten varios mapas de bits. Este mapa de bits se declara en el archivo .vsct junto con los iconos individuales disponibles en el mapa de bits. Vea la referencia de la [elemento de mapas de bits](../extensibility/bitmaps-element.md) para obtener más detalles.  
  
## <a name="adding-an-icon-to-a-command"></a>Agregar un icono a un comando  
 El siguiente procedimiento se da por supuesto que tiene un proyecto de VSPackage existente con un comando de menú. Para obtener más información sobre cómo hacerlo, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Cree un mapa de bits con una profundidad de color de 32 bits. Un icono siempre es 16 x 16 para que este mapa de bits debe ser de 16 píxeles de alto y un múltiplo de 16 píxeles de ancho.  
  
     Cada icono se coloca en el mapa de bits junto a la otra en una sola fila. Use el canal alfa para indicar los lugares de transparencia de cada icono.  
  
     Si utiliza una profundidad de color de 8 bits, utilice fucsia, `RGB(255,0,255)`, como la transparencia. Sin embargo, los iconos de colores de 32 bits se prefieren.  
  
2.  Copie el archivo de icono en el directorio de recursos en el proyecto de VSPackage. En el Explorador de soluciones, agregue el icono para el proyecto. (Seleccionar recursos y en el menú contextual, haga clic en Agregar y, a continuación, elemento existente y seleccione el archivo de icono).  
  
3.  Abra el archivo .vsct en el editor.  
  
4.  Agregar un `GuidSymbol` elemento con un nombre de **testIcon**. Crear un GUID (**herramientas / crear GUID**, a continuación, seleccione **formato del registro** y haga clic en Copiar) y péguelo en el `value` atributo. El resultado debería ser similar al siguiente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Agregar un `<IDSymbol>` del icono. El `name` atributo es el identificador del icono y el `value` indica su posición en la banda, si lo hay. Si hay un solo icono, agregue 1. El resultado debería ser similar al siguiente:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Crear un `<Bitmap>` en la `<Bitmaps>` sección del archivo .vsct para representar el mapa de bits que contiene los iconos.  
  
    -   Establecer el `guid` valor para el nombre de la `<GuidSymbol>` elemento creado en el paso anterior.  
  
    -   Establecer el `href` valor a la ruta de acceso relativa del archivo de mapa de bits (en este caso **recursos\\< nombre de archivo de icono\>**.  
  
    -   Establecer el `usedList` valor para el IDSymbol que creó anteriormente. Este atributo especifica una lista delimitada por comas de los iconos que se usará en el VSPackage. Los iconos no aparecen en la lista son compilación formulario excluidos.  
  
         El bloque de mapa de bits debe tener este aspecto:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Existente `<Button>` elemento, establezca la `Icon` elemento a los valores de GUIDSymbol y IDSymbol que creó anteriormente. Este es un ejemplo de un elemento de botón con esos valores:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  El icono de prueba. Compile la solución y comience la depuración. En la instancia experimental, busque el comando. Ahora, debería mostrar el icono que agregó.  
  
## <a name="see-also"></a>Vea también  
 [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)