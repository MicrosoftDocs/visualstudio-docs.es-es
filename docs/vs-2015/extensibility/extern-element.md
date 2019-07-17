---
title: Extern (elemento) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204396"
---
# <a name="extern-element"></a>Extern (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento externo hace referencia a los archivos de encabezado externo (. h) para combinar con el archivo .vsct en tiempo de compilación. Los archivos que van a combinarse deben estar en la ruta de acceso de inclusión especificado para el compilador VSCT o al que hace referencia un [elemento Include](../extensibility/include-element.md). Los archivos pueden ser otros archivos .vsct o archivos de encabezado de C++.  
  
 Las definiciones en archivos de encabezado deben tener el formato "#define [símbolo] [valor]" el valor puede ser otro símbolo, si se ha definido anteriormente. Las definiciones de pueden utilizarse en instrucciones condicionales de elementos de comando. Se descartará cualquier símbolo que no se utiliza realmente.  
  
 CommandTable (Elemento)  
Extern (Elemento)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|href|Necesario. La ruta de acceso al archivo de encabezado:<br /><br /> href="stdidcmd.h"|  
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Opcional. El idioma predeterminado de todos los [ \<cadenas >](../extensibility/strings-element.md) elementos en la tabla de comandos:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos, es decir, los elementos de menú, menús, barras de herramientas y cuadros combinados, que proporciona un paquete VSPackage en el IDE.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
