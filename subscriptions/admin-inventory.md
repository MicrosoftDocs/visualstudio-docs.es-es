---
title: Inventario de preproducción en la suscripción de Visual Studio | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 01/14/2021
ms.topic: conceptual
description: Obtenga información sobre la responsabilidad de los administradores de realizar inventarios de preproducción
ms.openlocfilehash: abcb3c8c1213885b5e543b05cf912c418acaa3f5
ms.sourcegitcommit: 4ee20054afe7bcf5c0aed504dec01e18059fbbd0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226492"
---
# <a name="inventory-of-pre-production-environment"></a>Inventario de entorno de preproducción
Las suscripciones de Visual Studio simplifican la administración de activos realizando un recuento de los usuarios en lugar de los dispositivos.

Los administradores de Visual Studio deben asignar Suscripciones de Visual Studio a **usuarios con nombre específicos**. **No se permiten** las convenciones de nomenclatura como Dev1 o Dev2 ni el uso de nombres de equipo como "FeatureTeam".

Estas son algunas maneras de simplificar el inventariado del entorno de preproducción:
- Revise las asignaciones de usuario. Microsoft proporciona un sitio web denominado [Portal de administración de Visual Studio](https://manage.visualstudio.com/) que le permite realizar un seguimiento de las asignaciones de suscripciones de Visual Studio.
- Use su versión de Active Directory local o basada en la nube para enumerar usuarios. Si usa Active Directory para administrar el acceso de usuarios, es posible que pueda identificar los usuarios de desarrollo y pruebas por su pertenencia al directorio.
- Use herramientas automatizadas para crear inventarios de sistemas. Es posible que también tenga que usar una herramienta de inventario de software para ayudarle a administrar sus activos de software y distinguir los entornos de preproducción de los entornos de producción. Muchos clientes con Microsoft System Center crean convenciones de nomenclatura para ayudar a automatizar esta parte del proceso de inventariado.
- Obtenga ayuda con la conciliación manual. Apunte al personal para que le ayude a conciliar los usuarios de desarrollo y pruebas con el entorno de desarrollo y pruebas.

> [!NOTE]
> No se otorgan licencias de software mediante suscripciones de Visual Studio para entornos de producción, incluido cualquier entorno al que accedan usuarios finales para otras acciones además de pruebas de aceptación o envío de comentarios, entornos que se conecten a una base de datos de producción, que permitan la recuperación ante desastres o la copia de seguridad de producción, o que se usen para producción durante períodos de actividad punta. Entre las excepciones a lo anterior se incluyen beneficios específicos para determinados niveles de suscripción, tal y como se describe en las [Notas del producto de licencias de Visual Studio](https://aka.ms/vslicensing).  

## <a name="resources"></a>Recursos
- [Notas sobre la concesión de licencias de Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Soporte técnico para suscripciones y administración de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Términos de las licencias por volumen](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre las responsabilidades de los administradores:
- [Responsabilidades del administrador](admin-responsibilities.md)
- [Administración de equipos grandes y contratistas externos](manage-teams.md)
- [Seguimiento de la asignación de usuarios y tramitación de pedidos](assignments-orders.md)
- Emplee [Uso máximo](maximum-usage.md) para realizar el seguimiento de los compromisos de compra