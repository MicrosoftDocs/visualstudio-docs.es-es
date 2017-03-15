---
title: "informaci&#243;n de HRESULT en c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HRESULT, VSPackages administrado"
  - "VSPackages, información de HRESULT"
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# informaci&#243;n de HRESULT en c&#243;digo administrado
La interacción entre el código administrado y COM puede causar problemas cuando se encuentran valores devueltos HRESULT.  
  
 En una interfaz COM, el valor devuelto HRESULT puede reproducir estos roles:  
  
-   Proporcione información de error \(por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>\).  
  
-   Proporcione información de estado sobre el comportamiento normal del programa.  
  
 Cuando a COM llama al código administrado, HRESULT puede producir estos problemas:  
  
-   Las funciones de COM que devuelven valores HRESULT menores que cero \(códigos de error\) generan excepciones.  
  
-   Los métodos COM que periódicamente devuelven dos o más códigos de éxito distinto como, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, no pueden ser completos.  
  
 Puesto que muchas de las funciones de COM [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] devuelven valores HRESULT menores que cero o códigos de éxito distintos, los ensamblados de interoperabilidad de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] se han escrito para que se conserven las firmas de método. Todos los métodos de interoperabilidad [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] son del tipo `int`. Los valores HRESULT se pasan a través de la capa de interoperabilidad sin modificar ni generar excepciones.  
  
 Puesto que la función COM devuelve un HRESULT al método administrado que lo llama, el método de llamada debe comprobar el valor HRESULT y generar excepciones según sea necesario.  
  
## Control de valores HRESULT devueltos al código administrado desde COM  
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. La clase <xref:Microsoft.VisualStudio.ErrorHandler> contiene el método <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, que produce una excepción de COM, dependiendo del valor HRESULT que se pasa.  
  
 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> generará una excepción siempre que se pase un valor HRESULT menor que cero. En los casos en los que los valores HRESULT sean aceptables y no se generen excepciones, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de probarlos. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, no se generará ninguna excepción.  
  
> [!NOTE]
>  La clase <xref:Microsoft.VisualStudio.VSConstants> contiene constantes para valores HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, y valores HRESULTS [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.<xref:Microsoft.VisualStudio.VSConstants> también proporciona los métodos <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, que corresponden a las macros SUCCEEDED y FAILED en COM.  
  
 Por ejemplo, considere la siguiente llamada de función, en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> es un valor devuelto aceptable, pero cualquier otro valor HRESULT menor que cero representa un error.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_1.vb)]
 [!code-cs[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_1.cs)]  
  
 Si hay más de un valor devuelto aceptable, los valores HRESULT adicionales solo se pueden anexar a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_2.vb)]
 [!code-cs[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_2.cs)]  
  
## Devolución de valores HRESULT a COM desde el código administrado  
 Si no se produce ninguna excepción, el código administrado devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> a la función COM que lo llamó. La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un argumento `null` inaceptable produce <xref:System.ArgumentNullException>.  
  
 Si no está seguro de la excepción que se debe generar pero conoce el valor HRESULT que desea devolver a COM, puede usar el método <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para generar la excepción adecuada. Esto funciona incluso con errores no estándar como, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> intenta asignar el valor HRESULT pasado a una excepción fuertemente tipada. Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT que se pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> desde el código administrado se devuelve a la función COM que lo llamó.  
  
> [!NOTE]
>  Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.  
  
## Vea también  
 [VSPackages administrado](../misc/managed-vspackages.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [How to: Map HRESULTs and Exceptions](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)   
 [Compilar componentes COM para la interoperación](http://msdn.microsoft.com/es-es/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages administrado](../misc/managed-vspackages.md)