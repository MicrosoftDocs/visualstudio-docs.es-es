---
title: Elemento extern | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ff198f5c4b574bf3a27ae1ee8fb6ffdd482c7f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extern-element"></a>Elemento externo
El elemento externo hace referencia a los archivos de encabezado externo (. h) para combinar con el archivo .vsct en tiempo de compilación. Los archivos que van a combinarse deben estar en la ruta de acceso de inclusión entregado al compilador VSCT o al que hace referencia un [elemento Include](../extensibility/include-element.md). Los archivos pueden estar otros archivos de vsct o archivos de encabezado de C++.  
  
 Las definiciones en archivos de encabezado deben tener el formato "#define [símbolo] [valor]" el valor puede ser otro símbolo si se ha definido previamente. Las definiciones de pueden utilizarse en instrucciones condicionales de elementos de comando. Se descartará cualquier símbolo no utilizada realmente.  
  
 Elemento CommandTable  
Elemento externo  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|href|Requerido. La ruta de acceso al archivo de encabezado:<br /><br /> href="stdidcmd.h"|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|lenguaje|Opcional. El idioma predeterminado de todos los [ \<cadenas >](../extensibility/strings-element.md) elementos en la tabla de comandos:<br /><br /> idioma = "en-us"|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos, es decir, elementos de menú, menús, barras de herramientas y cuadros combinados, que proporciona un paquete VSPackage al IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)