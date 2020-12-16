---
title: 'Cómo: firmar soluciones de Office'
description: Obtenga información sobre cómo conceder confianza a la solución de Microsoft Office mediante el uso de un certificado como prueba.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7451630570e6d557dc5d2b635d149ebc07cfb388
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528124"
---
# <a name="how-to-sign-office-solutions"></a>Cómo: firmar soluciones de Office
  Si firma una solución, puede conceder confianza a la solución mediante el certificado como evidencia. Puede usar el mismo certificado para varias soluciones y todas las soluciones serán de confianza sin actualizaciones adicionales de la Directiva de seguridad.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si edita manualmente los manifiestos de aplicación e implementación mediante el Herramienta de generación y edición de manifiestos (*mage.exe* y *mageui.exe*), debe volver a firmar los manifiestos para poder usarlos. Para obtener más información, vea [Cómo: volver a firmar manifiestos de aplicación y de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Firmar con un certificado
 Un certificado es un archivo que contiene una clave única y la identidad del editor de la solución. Puede adquirir certificados de una entidad de certificación o crear su propio certificado y hacer que una entidad de certificación la firme.

 Visual Studio firma las soluciones de Office con un certificado temporal para habilitar la depuración. No debe usar el certificado temporal en las soluciones implementadas como evidencia.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Para firmar una solución de Office mediante un certificado

1. En el menú **proyecto** , haga clic en **propiedades** de _solutionname_.

2. Haga clic en la pestaña **Firma** .

3. Seleccione **firmar los manifiestos de ClickOnce**.

4. Busque el certificado haciendo clic en **seleccionar del almacén** o **Seleccione desde el archivo** y navegue hasta el certificado.

5. Para comprobar que se está usando el certificado correcto, haga clic en **más detalles** para ver la información del certificado.

## <a name="see-also"></a>Consulte también

- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)
- [Página Firma, Diseñador de proyectos](../ide/reference/signing-page-project-designer.md)
