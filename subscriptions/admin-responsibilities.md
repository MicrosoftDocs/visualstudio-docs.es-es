---
title: Responsabilidades del administrador | Visual Studio Marketplace
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn about responsibilities of subscriptions administrators.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 92dcfe8b975596fc2f137630f6acfead6b935508
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2017
---
# <a name="administrator-overview"></a>Información general del administrador
## <a name="roles--responsibilities"></a>Roles y responsabilidades
A cambio de un descuento en el precio de productos y servicios de Microsoft, su organización acepta ciertas limitaciones y responsabilidades con respecto a las suscripciones de Visual Studio. Un administrador de Visual Studio tiene cuatro responsabilidades esenciales:
1.  **Comprender los beneficios y las restricciones de las suscripciones de Visual Studio.** Comprender correctamente que los beneficios pueden reducir los costos de hardware mediante el uso de servicios en la nube, así como reducir los costos de software con licencias por usuario para entornos de preproducción. 
2.  **Asignar suscripciones de Visual Studio a usuarios con nombre específicos.** El contrato requiere que las suscripciones de Visual Studio se asignen a usuarios con nombre específicos. Realice un seguimiento de los usuarios asignados para asegurarse de que pueden acceder y aprovechar al máximo los beneficios incluidos en su suscripción de Visual Studio.
3.  **Crear un inventario preciso del entorno de preproducción.** Esto es esencial para garantizar que todos los usuarios que interactúan con el software con licencia de Visual Studio tienen una licencia adecuada a su propia suscripción de Visual Studio. 
4.  **Realizar un seguimiento de los cambios de asignación y adquirir licencias adicionales según lo programado.** Los contratos de licencias por volumen (VL) de Microsoft ofrecen flexibilidad en el modo de usar y asignar suscripciones de Visual Studio. A cambio, deberá realizar un seguimiento de los cambios en el uso del software y las asignaciones de usuarios, y procesar los pedidos para adquirir licencias adicionales según la programación descrita en el contrato.

## <a name="benefits-and-limitations"></a>Beneficios y limitaciones
Las suscripciones de Visual Studio permiten a los miembros del equipo de desarrollo instalar y usar software para diseñar, desarrollar, probar, evaluar y demostrar otro software. Las licencias de software otorgadas mediante suscripciones de Visual Studio no son válidas para entornos de producción. 

|                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Licencias por usuario                     | Las licencias de Plataformas de MSDN y de todos los niveles de suscripciones de Visual Studio se conceden por usuario. Cada miembro del equipo de desarrollo que interaccione (instale, configure o acceda) con el software incluido con estos productos y servicios necesitará su propia suscripción de Visual Studio.                                                                                                                                                                                                                                                                                                                                  |
| Instalaciones ilimitadas                  | Cada usuario con licencia podrá instalar y usar el software en cualquier número de dispositivos para diseñar, desarrollar, probar, evaluar y demostrar el software. La excepción es Microsoft Office, cuya licencia se otorga para un escritorio. El software de Visual Studio con licencia se puede instalar y usar en el trabajo, el hogar, el centro educativo y en dispositivos de la oficina de un cliente o en un hardware dedicado hospedado por terceros.                                                                                                                                                                                                                                  |
| No está diseñado para entornos de producción | No se otorgan licencias de software mediante suscripciones de Visual Studio para entornos de producción, incluido cualquier entorno al que accedan usuarios finales para otras acciones además de pruebas de aceptación o envío de comentarios, entornos que se conecten a una base de datos de producción, que permitan la recuperación ante desastres o la copia de seguridad de producción, o que se usen para producción durante períodos de actividad punta. Entre las excepciones a lo anterior se incluyen beneficios específicos para determinados niveles de suscripción, tal y como se describe en las [Notas del producto de licencias de Visual Studio](http://aka.ms/vslicensing).                                                                                            |
| Reasignación de licencias                     | Cuando un usuario abandona un equipo y ya no requiere una licencia, puede volver a asignar esa licencia transcurridos 90 días. Al reasignar una licencia, no se sustituirán las claves de producto que ya se hayan usado. Se trata de una funcionalidad diferente de la que había en el Centro de servicio de licencias por volumen (VLSC). Se restablecerá cualquier ventaja que el usuario original haya usado, como el aprendizaje de Pluralsight.                                                                                                                                                                                                                                                 |
| Excepción para usuarios finales                  | Al final de un proyecto de desarrollo de software, los usuarios finales normalmente revisan una aplicación y determinan si cumple los criterios necesarios para su lanzamiento. Este proceso se denomina pruebas de aceptación de usuario (UAT). Los miembros del equipo, como un patrocinador o un jefe de producto o de negocio, pueden actuar como representantes de los usuarios finales. Los usuarios finales que no tienen una suscripción de Visual Studio podrían acceder al software para UAT si el uso del software cumple en todo caso con los términos de licencia de Visual Studio. Es raro que un usuario cuyo rol principal sea diseñar, desarrollar o probar el software se califique también como “usuario final”. |

## <a name="inventory-of-pre-production-environment"></a>Inventario de entorno de preproducción
Las suscripciones de Visual Studio simplifican la administración de activos realizando un recuento de los usuarios en lugar de los dispositivos.

Los administradores de Visual Studio deben asignar suscripciones de Visual Studio a **usuarios con nombre específicos**. Las convenciones de nomenclatura, como Dev1, Dev2 o Dev3 **no se permiten**.

Estas son algunas maneras de simplificar el inventariado del entorno de preproducción:
- Revise las asignaciones de usuario. Microsoft proporciona un sitio web denominado [Portal de administración de Visual Studio](https://manage.visualstudio.com/) que le permite realizar un seguimiento de las asignaciones de suscripciones de Visual Studio.
- Use su versión de Active Directory local o basada en la nube para enumerar usuarios. Si usa Active Directory para administrar el acceso de usuarios, es posible que pueda identificar los usuarios de desarrollo y pruebas por su pertenencia al directorio.
- Use herramientas automatizadas para crear inventarios de sistemas. Es posible que también tenga que usar una herramienta de inventario de software para ayudarle a administrar sus activos de software y distinguir los entornos de preproducción de los entornos de producción. Muchos clientes con Microsoft System Center crean convenciones de nomenclatura para ayudar a automatizar esta parte del proceso de inventariado.
- Obtenga ayuda con la conciliación manual. Apunte al personal para que le ayude a conciliar los usuarios de desarrollo y pruebas con el entorno de desarrollo y pruebas. 

## <a name="large-teams-and-external-contractors"></a>Equipos grandes y contratistas externos
Los administradores de suscripciones de Visual Studio se encargan de garantizar que cada usuario que interactúa con el software con licencia de Visual Studio tenga una licencia acorde a su propia suscripción de Visual Studio.
### <a name="internal-teams"></a>Equipos internos
Normalmente, las organizaciones de software modernas incluyen a partes interesadas de varios grupos. Identifique contactos de cada grupo que puedan ayudarle a realizar un seguimiento de los cambios y el inventario de usuarios. Aunque cada organización es diferente, una lista típica de equipos implicados en el desarrollo podría incluir:
- Equipos de ingeniería de software. 
- Equipos de negocio, incluidos propietarios de producto y analistas de negocios.
- Equipos de administración de proyectos. 
- Equipos de calidad, incluido el personal de preguntas y respuestas y los encargados de pruebas manuales.
- Operaciones de TI, incluidos los administradores de infraestructura de preproducción y laboratorio.

### <a name="external-contractors-and-partners"></a>Socios y contratistas externos
Los contratistas externos pueden traer licencias para interaccionar con el entorno de Visual Studio con licencia. Los miembros de Microsoft Certified Partners podrán recibir unas pocas suscripciones gratuitas de Visual Studio para uso interno. Sin embargo, estas suscripciones no abarcan actividades lucrativas, como desarrollar software personalizado para un cliente. Pida a los socios que le envíen una carta certificada en la que se explique qué licencias están proporcionando y cuáles necesitan que usted adquiera.

## <a name="track-user-assignment-and-process-orders"></a>Seguimiento de la asignación de usuarios y tramitación de pedidos
Los administradores de suscripciones de Visual Studio deberán realizar un seguimiento del uso de Visual Studio y tramitar pedidos para cualquier incremento en el uso según la programación descrita en su Contrato de licencia por volumen o en el Contrato de productos y servicios de Microsoft. El nuevo Portal de administración de suscripciones de Visual Studio ha simplificado esta tarea con una útil herramienta de seguimiento que muestra las licencias disponibles y las usadas.
### <a name="high-water-mark-of-usage"></a>Límite máximo de uso
**La obligación de su compañía de comprar suscripciones de Visual Studio surte efecto inmediatamente cuando:**
- Se asigna una licencia a un usuario.
- Un usuario interactúa con el software de Visual Studio.

La obligación de compra completa viene determinada por el **límite máximo de uso**. Este límite máximo está destinado a asignaciones de usuarios por día o a usuarios que interactúan con el software de Visual Studio, lo que antes alcance el límite.
1.  Los administradores de suscripciones de Visual Studio pueden aumentar el límite máximo de uso mediante la asignación de suscripciones de Visual Studio a usuarios individuales.
2.  Los administradores de suscripciones de Visual Studio suscripciones pueden volver a asignar las suscripciones de un suscriptor a otro si han transcurrido 90 días desde el momento de la asignación original. Para evitar un límite máximo artificial, quite primero la suscripción existente y después agregue una nueva.
3.  Los administradores de suscripciones de Visual Studio pueden cambiar el nivel de suscripción asignada para un usuario individual, lo que supondría una disminución en una asignación y un aumento en otra. Cuando se reduce el nivel de suscripción asignada a un suscriptor, el usuario debe dejar de usar inmediatamente y desinstalar todo aquello que se encuentre solo en el nivel de suscripción de nivel más alto. 

### <a name="open-license-and-open-value"></a>Open License y Open Value
Las suscripciones se pueden asignar a través de otro programa de licencias por volumen de Microsoft, como Microsoft Open License u Open Value. Si usa estos programas, debe procesar su pedido para los usuarios adicionales durante el mes en el que los usuarios (empleados o contratistas externos) empiezan a interactuar con el software con licencia de Visual Studio.
### <a name="enterprise-agreements"></a>Contratos Enterprise
Los contratos Enterprise de Microsoft (EA), MPSA y Select Plus ofrecen flexibilidad en cuanto al uso del software y las licencias de Visual Studio con el paso del tiempo. Los administradores de Visual Studio deben realizar un pedido “true up” anual para llevar sus licencias de software hasta el nivel máximo de uso establecido durante el periodo del contrato.