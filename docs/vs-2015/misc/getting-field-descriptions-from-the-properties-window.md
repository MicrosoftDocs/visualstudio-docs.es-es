---
title: Obtener descripciones de campos de la ventana Propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703981"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Obtener descripciones de los campos de la ventana Propiedades
En la parte inferior de la ventana **Propiedades** , un área de descripción muestra información relacionada con el campo de la propiedad seleccionada. Esta característica está activada de forma predeterminada. Si quiere ocultar el campo de descripción, haga clic con el botón derecho en la ventana **Propiedades** y haga clic en **Descripción**. Al hacerlo, también se quita la marca de verificación junto al título **Descripción** de la ventana de menú. Puede volver a mostrar el campo siguiendo los mismos pasos para volver a activar **Descripción** .  
  
 La información del campo descripción proviene de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interfaz, coclase, etc. puede tener un atributo `helpstring` sin localizar en la biblioteca de tipos. La ventana **propiedades** recupera la cadena de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .  
  
### <a name="to-specify-localized-help-strings"></a>Para especificar cadenas de ayuda localizadas  
  
1. Agregue el atributo `helpstringdll` a la instrucción de la biblioteca en la biblioteca de tipos (`typelib`).  
  
   > [!NOTE]
   > Este paso es opcional si la biblioteca de tipos está en un archivo de biblioteca de objetos (.olb).  
  
2. Especifique atributos `helpstringcontext` para las cadenas. También puede especificar atributos `helpstring` .  
  
    Estos atributos son distintos de los atributos `helpfile` y `helpcontext` , que se encuentran en los temas de Ayuda del archivo .chm real.  
  
   Para recuperar la información de la descripción que se va a mostrar para el nombre de la propiedad resaltada, la ventana **propiedades** llama a <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> la propiedad que está seleccionada y especifica el `lcid` atributo deseado para la cadena de salida. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> busca el archivo .dll especificado en el atributo `helpstringdll` y llama a la función `DLLGetDocumentation` en dicho archivo .dll con el contexto especificado y el atributo `lcid`.  
  
   La signatura y la implementación de `DLLGetDocumentation` son:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 La función `DLLGetDocumentation` debe ser una exportación definida en el archivo .def para la DLL.  
  
 Internamente, se crea un archivo .olb, que en realidad es una DLL. Esta DLL contiene un recurso, el archivo de biblioteca de tipos (.tlb) y una función exportada, `DLLGetDocumentation`.  
  
 En el caso de los archivos .olb, el atributo `helpstringdll` es opcional porque es el mismo archivo que contiene el propio archivo .tlb.  
  
 Para obtener cadenas que aparezcan en el panel **Descripciones** , por tanto, lo mínimo que debe hacer es especificar el atributo `helpstring` en la biblioteca de tipos. Si quiere que estas cadenas se localicen, debe especificar el atributo `helpstringdll` (opcional) y el atributo `helpstringcontext` (obligatorio) e implementar `DLLGetDocumentation`.  
  
 No hay interfaces adicionales que deban implementarse al obtener información localizada a través del atributo `helpstringcontext` y la función `DLLGetDocumentation`del archivo .idl.  
  
 Otra manera de obtener el nombre y la descripción localizados de una propiedad es implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Para obtener más información sobre la implementación de este método, consulte [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Campos e interfaces de la ventana Propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)