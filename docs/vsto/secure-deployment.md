---
title: Implementación segura
description: Obtenga información acerca de cómo debe proporcionar pruebas sobre las que basar una decisión de confianza mediante la firma de la solución con un certificado o mediante la clave de mensaje de confianza de ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b47a18aa3e791d446abc2a57b6aad1f139924ebf
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528471"
---
# <a name="secure-deployment"></a>Implementación segura
  Al crear una solución de Office, el equipo de desarrollo se actualiza automáticamente para permitir que se ejecute el código del proyecto. Sin embargo, al implementar la solución, debe proporcionar una prueba en la que basar una decisión de confianza mediante la firma de la solución con un certificado o mediante la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clave de mensaje de confianza. Para obtener más información, vea [conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 En el caso de las personalizaciones de nivel de documento, si implementa el documento en una ubicación de red, también debe agregar la ubicación del documento a la lista de ubicaciones de confianza en el centro de confianza de la aplicación de Office. Para obtener más información sobre cómo establecer permisos de documento en los equipos de los usuarios finales, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Impedir que las soluciones de Office ejecuten código
 Los administradores pueden utilizar el registro para evitar que todas las soluciones de Office se ejecuten en un equipo. Cuando se abre una solución de Office que tiene extensiones de código administrado, el Visual Studio Tools para el tiempo de ejecución de Office comprueba si existe una entrada con el nombre `Disabled` en una de las siguientes claves del registro en el equipo:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Para evitar que las soluciones de Office ejecuten código, cree una `Disabled` entrada en una o ambas claves del registro y especifique uno de los siguientes tipos de datos y valores para `Disabled` :

- REG_SZ o REG_EXPAND_SZ que se establece en cualquier cadena distinta de "0" (cero).

- REG_DWORD que se establece en cualquier valor distinto de 0 (cero).

  Para permitir que las soluciones de Office ejecuten código, establezca ambas `Disabled` entradas en 0 (cero) o elimine las entradas del registro.

## <a name="see-also"></a>Consulte también
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Preparar los equipos para ejecutar o hospedar soluciones de Office](/previous-versions/bb772092(v=vs.110))
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)