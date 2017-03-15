---
title: "Soluci&#243;n de problemas de excepciones: System.Runtime.InteropServices.COMException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHCOM"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COMException (clase)"
ms.assetid: 14b6de51-e039-4db7-9321-06c9e16e328a
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Runtime.InteropServices.COMException
Cuando una llamada al método COM devuelve un resultado HRESULT desconocido, se produce una excepción <xref:System.Runtime.InteropServices.COMException>.  
  
## Sugerencias asociadas  
 **Compruebe la propiedad ErrorCode de la excepción para determinar el resultado HRESULT devuelto por el objeto COM.**  
 Cuando el motor en tiempo de ejecución encuentra un resultado HRESULT desconocido, se produce una excepción <xref:System.Runtime.InteropServices.COMException>, que incluye una propiedad `ErrorCode` pública que contiene el valor HRESULT que devolvió la llamada. Si el motor en tiempo de ejecución dispone de un mensaje de error, se devuelve dicho mensaje al llamador. Sin embargo, si el desarrollador de componentes COM no incluye un mensaje de error, el motor en tiempo de ejecución devuelve el valor HRESULT de ocho dígitos en lugar de una cadena de mensaje. HRESULT permite al llamador determinar la causa de la excepción. Para obtener más información, consulta [How to: Map HRESULTs and Exceptions](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md).  
  
 **Deshabilitar el proceso de hospedaje.**  
 COM permite la comunicación entre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y el proceso de hospedaje. Dado que se utiliza antes de la ejecución de código, una llamada a `CoInitializeSecurity` hace que se produzca esta excepción.  
  
### Comentarios  
 El Common Language Runtime \(CLR\) transforma los resultados conocidos de HRESULT en excepciones de .NET, lo que permite que los objetos COM devuelvan una información de errores significativa a los clientes administrados. El resultado HRESULT de una asignación de excepción también funciona en sentido contrario, ya que devuelve HRESULT específicos a clientes no administrados.  
  
 Al pasar parámetros enlazados en tiempo de ejecución a métodos de objetos de Microsoft Office, se puede producir una excepción <xref:System.Runtime.InteropServices.COMException> cuando los objetos son objetos COM. El enlazador en tiempo de ejecución supone que tales llamadas al método implican un parámetro `ByRef` y que la propiedad que se pasa tiene un descriptor de acceso `Set`. Si la propiedad no tiene un descriptor de acceso, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] genera una excepción <xref:System.MissingMethodException> \(HRESULT CORE\_E\_MISSINGMETHOD\). Para evitar este comportamiento, utilice los objetos enlazados en tiempo de compilación o pase una variable en lugar de una propiedad del objeto.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.COMException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Controlar excepciones de interoperabilidad COM](../Topic/Handling%20COM%20Interop%20Exceptions.md)