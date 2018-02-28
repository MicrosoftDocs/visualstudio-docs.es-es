---
title: Comandos de elemento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c5cce390ad786ad530153e1850850509990b039
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="commands-element"></a>Elemento Commands
Representa la colección de comandos en la barra de herramientas de VSPackage. La colección puede tener hasta cinco subsecciones, como se indica a continuación: menús, grupos, botones, combinaciones y mapas de bits.  
  
 Cada elemento de secundario subsección, por ejemplo, \<menú >, se identifica mediante un identificador de comando único que es un GUID y un par de identificador numérico. El GUID identifica el "conjunto de comandos" y se utiliza para agrupar los comandos relacionados lógicamente. El VSPackage debe definir su propio conjunto de comandos establecido para evitar conflictos con los identificadores de comando que se definen mediante otros VSPackages.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|paquete|Un GUID que identifica el VSPackage que se muestran los comandos.<br /><br /> Por ejemplo, empaquetar = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
|[Groups (Elemento)](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos en un paquete VSPackage.|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Agrupa elementos de botón.|  
|[Bitmaps (Elemento)](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|  
|[Combos (Elemento)](../extensibility/combos-element.md)|Agrupa elementos combinados.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un VSPackage proporciona al IDE. Posibles elementos son elementos de menú, menús, barras de herramientas y cuadros combinados.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar un [Commands, elemento](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)