---
title: Extern (elemento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc48dc471dab06bf18c0edf622cfa18e7159eaab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895264"
---
# <a name="extern-element"></a>Extern (elemento)
El elemento externo hace referencia a cualquier encabezado externo (*.h*) archivos para combinar con el *.vsct* archivo en tiempo de compilación. Los archivos que van a combinarse deben estar en la ruta de acceso de inclusión especificado para el compilador VSCT o al que hace referencia un [elemento Include](../extensibility/include-element.md). Es pueden que los archivos de otros *.vsct* archivos o archivos de encabezado de C++.  
  
 Las definiciones en archivos de encabezado deben tener el formato "#define [símbolo] [valor]" el valor puede ser otro símbolo, si se ha definido anteriormente. Las definiciones de pueden utilizarse en instrucciones condicionales de elementos de comando. Se descartará cualquier símbolo que no se utiliza realmente.  
  
 CommandTable (Elemento)  
Extern (Elemento)  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|href|Obligatorio. La ruta de acceso al archivo de encabezado:<br /><br /> href="stdidcmd.h"|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|lenguaje|Opcional. El idioma predeterminado de todos los [ \<cadenas >](../extensibility/strings-element.md) elementos en la tabla de comandos:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos, es decir, los elementos de menú, menús, barras de herramientas y cuadros combinados, que proporciona un paquete VSPackage en el IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Los comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)