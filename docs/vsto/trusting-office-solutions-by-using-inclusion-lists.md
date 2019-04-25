---
title: Confiar en soluciones de Office mediante listas de inclusión
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 34b4ed5dbc0996239e73db38f1d6bea9e43d6de4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640602"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Confiar en soluciones de Office mediante listas de inclusión
  Las listas de inclusión permiten a los usuarios decidir si las soluciones de Office firmadas con un certificado que identifique al publicador son fiables. Las listas de inclusión son específicas del usuario y se pueden usar en las personalizaciones de nivel de documento y en los complementos VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Cuando un usuario inicia una solución de Office que no se haya indicado como fiable, la solución de Microsoft Office le solicita que confirme si confía en esa solución mediante una pregunta de seguridad de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Si el usuario decide que la solución es fiable, la personalización se ejecuta y no se vuelve a preguntar al usuario.

## <a name="inclusion-list-and-windows-installer"></a>Lista de inclusión y Windows Installer
 Instalar soluciones de Office en el *archivos de programa* directory mediante Windows Installer requiere derechos de administrador. Para soluciones de Office en el *archivos de programa* directorio, Visual Studio Tools para Office runtime ya no comprueba la lista de inclusión porque ya se ha concedido permisos FullTrust a las soluciones de Office.

## <a name="clickonce-trust-prompt"></a>Solicitud de fiabilidad de ClickOnce
 Si se usa la implementación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] para soluciones de Office, los administradores podrán configurar el nivel del mensaje de solicitud de fiabilidad para permitir que se realice la solicitud, para deshabilitarla o para solicitar un certificado de confianza. Esta configuración se realiza con una clave de registro que controla el acceso a la lista de inclusión.

 Si se deshabilita la solicitud, sólo se pueden instalar las soluciones que dispongan de un certificado de confianza. Si el nivel de la solicitud se establece como “Authenticode necesario”, la solución se debe firmar con un certificado procedente de una autoridad conocida, pero no será necesario ningún certificado que vincule a una autoridad raíz de confianza (es decir, un certificado de confianza). Si se permite la solicitud, la solución se podrá firmar mediante un certificado cuya identidad sea desconocida. En este caso, la decisión de decidir si se confía en ese elemento o no, se deja al usuario final; es más, basta con un certificado temporal para instalar una solución.

 Para obtener más información, vea [Cómo: Configurar la seguridad de la lista de inclusión](../vsto/how-to-configure-inclusion-list-security.md) y tabla 2 sobre los efectos que nivel de registro clave valor iniciar tienen, en [editores de confianza de ClickOnce configurar](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="structure-of-the-inclusion-list"></a>Estructura de la lista de inclusión
 Una entrada de lista de inclusión válida tiene dos partes: una ruta de acceso al manifiesto de implementación y la clave pública que se usa para firmar la solución. Una vez agregada una solución a la lista de inclusión, se considera de confianza. Cuando se ejecuta la solución de Office, la aplicación de Office compara la clave pública de la lista de inclusión con la clave de firma del manifiesto de implementación, para comprobar que la solución que se está ejecutando actualmente es igual que la versión de confianza original.

## <a name="see-also"></a>Vea también
- [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
