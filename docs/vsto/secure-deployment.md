---
title: "Implementación segura | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f52c6d26132490defafdf87639e0f1731ea90640
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="secure-deployment"></a>Implementación segura
  Cuando se crea una solución de Office, el equipo de desarrollo se actualiza automáticamente para permitir que el código en el proyecto se ejecute. Sin embargo, al implementar la solución, debe proporcionar evidencia en el que se va a basar una decisión de confianza, la solución con un certificado de firma, o use el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave del mensaje de confianza. Para obtener más información, consulte [otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para las personalizaciones de nivel de documento, si implementa el documento en una ubicación de red, también debe agregar la ubicación del documento a la lista de ubicaciones de confianza en el centro de confianza de la aplicación de Office. Para obtener más información acerca de cómo establecer permisos de documento en el usuario final de los equipos, consulte [otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Impide que se ejecuta código de las soluciones de Office  
 Los administradores pueden usar el registro para impedir que todas las soluciones de Office se ejecuten en un equipo. Cuando una solución de Office que tiene extensiones de código administrado se abre, Visual Studio Tools para las comprobaciones de Office en tiempo de ejecución si una entrada con el nombre `Disabled` existe en una de las siguientes claves del registro en el equipo:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Para evitar que las soluciones de Office se ejecuten código, cree un `Disabled` entrada en una o ambas de estas claves del registro y especifique uno de los siguientes tipos de datos y valores para `Disabled`:  
  
-   Un valor REG_SZ o REG_EXPAND_SZ que se establece en cualquier cadena distinta de "0" (cero).  
  
-   REG_DWORD que se establece en cualquier valor distinto de 0 (cero).  
  
 Para habilitar las soluciones de Office ejecutar el código, establezca ambos el `Disabled` entradas en 0 (cero), o eliminar las entradas del registro.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Preparar los equipos para ejecutar u hospedar soluciones de Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Protección de soluciones de Office](../vsto/securing-office-solutions.md)  
  
  