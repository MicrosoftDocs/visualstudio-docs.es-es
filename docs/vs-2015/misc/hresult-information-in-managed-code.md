---
title: Información de HRESULT en código administrado | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566212"
---
# <a name="hresult-information-in-managed-code"></a>Información de HRESULT en código administrado
La interacción entre el código administrado y COM puede causar problemas cuando se encuentran valores devueltos HRESULT.  
  
 En una interfaz COM, el valor devuelto HRESULT puede reproducir estos roles:  
  
-   Proporcione información de error (por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
-   Proporcione información de estado sobre el comportamiento normal del programa.  
  
 Cuando a COM llama al código administrado, HRESULT puede producir estos problemas:  
  
-   Las funciones de COM que devuelven valores HRESULT menores que cero (códigos de error) generan excepciones.  
  
-   Los métodos COM que periódicamente devolución dos o más códigos de éxito distintos, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, no puede ser completo.  
  
 Dado que muchos de los [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funciones COM devuelven valores HRESULT menor que cero o devolución códigos de éxito distintos, el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ensamblados de interoperabilidad se han escrito para que se conservan las firmas de método. Todos los [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] son métodos de interoperabilidad de `int` tipo. Los valores HRESULT se pasan a través de la capa de interoperabilidad sin modificar ni generar excepciones.  
  
 Puesto que la función COM devuelve un HRESULT al método administrado que lo llama, el método de llamada debe comprobar el valor HRESULT y generar excepciones según sea necesario.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM  
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. El <xref:Microsoft.VisualStudio.ErrorHandler> clase contiene la <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> método, que produce una excepción de COM, dependiendo del valor de HRESULT se pasa a él.  
  
 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> producirá una excepción cuando se pasa un valor HRESULT que tiene un valor menor que cero. En casos donde HRESULT sean aceptables y no deben producir ninguna excepción, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de que se prueban los valores. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, se produce ninguna excepción.  
  
> [!NOTE]
>  El <xref:Microsoft.VisualStudio.VSConstants> clase contiene constantes para valores HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, y [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] valores HRESULT, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> También proporciona la <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> métodos, que corresponden a las macros SUCCEEDED y FAILED en COM.  
  
 Por ejemplo, considere la siguiente llamada de función en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> es un valor devuelto aceptable, pero cualquier otro valor HRESULT menor que cero representa un error.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Si hay de más de un aceptables valores devueltos, los valores HRESULT adicionales solo se pueden anexar a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Devolución de valores HRESULT a COM desde el código administrado  
 Si se produce ninguna excepción, el código administrado devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> a la función COM que lo llamó. La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un inaceptable `null` argumento produce una <xref:System.ArgumentNullException>.  
  
 Si no está seguro de qué excepción que se inicia, pero conoce el valor HRESULT que desea devolver a COM, puede usar el <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> método inicie una excepción adecuada. Esto funciona incluso con un error no estándar, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Si intenta asignar el valor HRESULT pasado a una excepción fuertemente tipada. Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT se pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> desde código administrado, se devuelve a la función COM que lo llamó.  
  
> [!NOTE]
>  Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages administrado](../misc/managed-vspackages.md)   
 [Interoperar con código no administrado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Cómo: asignar resultados HRESULT y excepciones](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Creación de componentes COM para la interoperación](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages administrado](../misc/managed-vspackages.md)