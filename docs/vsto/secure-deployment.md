---
title: Implementación segura
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0ed351bf15ec257f79e226958b38e46ac769d0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673909"
---
# <a name="secure-deployment"></a>Implementación segura
  Cuando se crea una solución de Office, el equipo de desarrollo se actualiza automáticamente para permitir que el código en el proyecto se ejecute. Sin embargo, al implementar la solución, debe proporcionar evidencia de que se va a basar una decisión de confianza para la solución con un certificado de firma o usar el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave del mensaje de confianza. Para obtener más información, consulte [conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Para las personalizaciones de nivel de documento, si implementa el documento en una ubicación de red, también debe agregar la ubicación del documento a la lista de ubicaciones de confianza en el centro de confianza de la aplicación de Office. Para obtener más información sobre cómo establecer permisos de documentos en equipos de usuario final, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Impedir que se ejecute código soluciones de Office  
 Los administradores pueden usar el registro para evitar que todas las soluciones de Office que se ejecutan en un equipo. Cuando una solución de Office que tiene extensiones de código administrado se abre, Visual Studio Tools para las comprobaciones en tiempo de ejecución de Office si una entrada con el nombre `Disabled` existe en una de las siguientes claves del registro en el equipo:  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
 Para evitar que las soluciones de Office se ejecute código, cree un `Disabled` entrada en una o ambas de estas claves del registro y especifique uno de los siguientes tipos de datos y valores para `Disabled`:  
  
-   Un valor REG_SZ o REG_EXPAND_SZ que se establece en cualquier cadena distinta de "0" (cero).  
  
-   REG_DWORD que se establece en cualquier valor distinto de 0 (cero).  
  
 Para habilitar las soluciones de Office ejecutar el código, establezca ambos el `Disabled` entradas en 0 (cero), o eliminar las entradas del registro.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Preparar los equipos para ejecutar u hospedar soluciones de Office](http://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)  
  
  