---
title: Comandos de elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31f34dbf974ef860ddabd29af0e94b3c65a11f32
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231013"
---
# <a name="commands-element"></a>Elemento Commands
Representa la colección de comandos en la barra de herramientas de VSPackage. La colección puede tener hasta cinco subsecciones, como sigue: menús, botones, grupos, combos y mapas de bits.  
  
 Cada elemento de secundario subsección, por ejemplo, \<menú >, se identifica mediante un identificador de comando único que es un GUID y un par de identificador numérico. El GUID identifica el conjunto de comandos"" y se usa para agrupar los comandos relacionados lógicamente. El VSPackage debe definir su propio conjunto de comandos para evitar conflictos con identificadores de comando que se definen por otros VSPackages.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
|paquete|Un GUID que identifica el paquete VSPackage que proporciona los comandos.<br /><br /> Por ejemplo, los paquetes = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos en un VSPackage.|  
|[Buttons (elemento)](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|  
|[Bitmaps (elemento)](../extensibility/bitmaps-element.md)|Agrupa los elementos de mapa de bits.|  
|[Combos (elemento)](../extensibility/combos-element.md)|Agrupa los elementos del cuadro combinado.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que un paquete VSPackage proporciona al IDE. Posibles elementos son elementos de menú, barras de herramientas, menús y cuadros combinados.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar un [elemento Commands](../extensibility/commands-element.md).  
  
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
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)