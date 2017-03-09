---
title: "Obtener descripciones de los campos de la ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventana Propiedades, descripciones de campos"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Obtener descripciones de los campos de la ventana Propiedades
En la parte inferior de la ventana **Propiedades**, un área de descripción muestra información relacionada con el campo de la propiedad seleccionada. Esta característica está activada de forma predeterminada. Si quiere ocultar el campo de descripción, haga clic con el botón derecho en la ventana **Propiedades** y haga clic en **Descripción**. Al hacerlo, también se quita la marca de verificación junto al título **Descripción** de la ventana de menú. Puede volver a mostrar el campo siguiendo los mismos pasos para volver a activar **Descripción**.  
  
 La información del campo descripción proviene de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interfaz, coclase, etc. puede tener un atributo `helpstring` sin localizar en la biblioteca de tipos. La ventana **Propiedades** recupera la cadena de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### Para especificar cadenas de ayuda localizadas  
  
1.  Agregue el atributo `helpstringdll` a la instrucción de la biblioteca en la biblioteca de tipos \(`typelib`\).  
  
    > [!NOTE]
    >  Este paso es opcional si la biblioteca de tipos está en un archivo de biblioteca de objetos \(.olb\).  
  
2.  Especifique atributos `helpstringcontext` para las cadenas. También puede especificar atributos `helpstring`.  
  
     Estos atributos son distintos de los atributos `helpfile` y `helpcontext`, que se encuentran en los temas de Ayuda del archivo .chm real.  
  
 Para recuperar la información de descripción que se mostrará para el nombre de la propiedad resaltada, la ventana **Propiedades** llama a la función <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> de la propiedad seleccionada y especifica el atributo `lcid` deseado para la cadena de salida. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> busca el archivo .dll especificado en el atributo `helpstringdll` y llama a la función `DLLGetDocumentation` en dicho archivo .dll con el contexto especificado y el atributo `lcid`.  
  
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
  
 Internamente, se crea un archivo .olb, que en realidad es una DLL. Esta DLL contiene un recurso, el archivo de biblioteca de tipos \(.tlb\) y una función exportada, `DLLGetDocumentation`.  
  
 En el caso de los archivos .olb, el atributo `helpstringdll` es opcional porque es el mismo archivo que contiene el propio archivo .tlb.  
  
 Para obtener cadenas que aparezcan en el panel **Descripciones**, por tanto, lo mínimo que debe hacer es especificar el atributo `helpstring` en la biblioteca de tipos. Si quiere que estas cadenas se localicen, debe especificar el atributo `helpstringdll` \(opcional\) y el atributo `helpstringcontext` \(obligatorio\) e implementar `DLLGetDocumentation`.  
  
 No hay interfaces adicionales que deban implementarse al obtener información localizada a través del atributo `helpstringcontext` y la función `DLLGetDocumentation` del archivo .idl.  
  
 Otra manera de obtener el nombre y la descripción localizados de una propiedad es implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Para obtener más información sobre la implementación de este método, consulte [Interfaces y campos de la ventana de propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Interfaces y campos de la ventana de propiedades](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Extender propiedades](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)