---
title: Adquisición de suscripciones de nube de Visual Studio para CSP
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: d2ab13ed-ef79-4ef0-8736-eccd04bc6020
ms.date: 10/21/2020
ms.topic: conceptual
description: Información para proveedores de soluciones en la nube sobre cómo comprar y administrar suscripciones de nube de Visual Studio para sus clientes.
ms.openlocfilehash: 632e407aa4455b7c2a87299cc8811bc996c8d5b6
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353270"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Adquirir y administrar suscripciones de nube de Visual Studio para los clientes
Los partners que participen en el programa [Proveedor de soluciones en la nube (CSP)](https://partner.microsoft.com/cloud-solution-provider) pueden adquirir suscripciones de nube de Visual Studio Enterprise y de Professional de Visual Studio para sus clientes.

[Comparación de las opciones de suscripción de nube](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Microsoft ya no ofrece suscripciones anuales ni de Visual Studio Professional ni de Visual Studio Enterprise en las suscripciones de nube. Esto no supone cambio alguno en la experiencia actual de los clientes y ni en su capacidad para renovar, aumentar, reducir o cancelar las suscripciones. Conviene que los clientes nuevos vayan a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) para explorar las diferentes opciones de compra de Visual Studio.

## <a name="prerequisites"></a>Requisitos previos
En primer lugar, hay que configurar el inquilino del cliente en el Centro de partners y crear una suscripción de Azure para dicho inquilino.

[Más información](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>¿Quién puede comprar suscripciones de Visual Studio?
Cualquier persona con [acceso de propietario o de colaborador](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) a la suscripción de Azure puede comprar suscripciones de Visual Studio.

## <a name="how-to-buy"></a>Cómo comprarlas

1. Inicie sesión en el [Centro de partners de Microsoft](https://partnercenter.microsoft.com).
0. Seleccione **Clientes** y seleccione el cliente para el que vaya a realizar la compra.
0. Seleccione **Administración de servicios** .
0. Elija **Visual Studio Marketplace** .
0. Constate que el nombre de su cliente aparece en la esquina superior derecha.
0. Seleccione **Suscripciones** .
0. Seleccione Enterprise o Professional para Visual Studio.
0. Elija **Comprar** .
0. Escoja la suscripción de Azure a la que se va a facturar la compra.
0. Escriba el número de usuarios que el cliente necesita.
0. Revise el pedido y **confírmelo** .

>[!NOTE]
> Hay que seguir estos pasos cada vez que se adquieran suscripciones de Visual Studio como CSP. En este momento, no existe ninguna API que automatice esta compra.

Tras confirmar la compra, puede elegir **Administrar** para asignar suscripciones a los usuarios finales del cliente.  También puede tener acceso al portal de administración de suscripciones desde el Centro de partners; para ello, seleccione **Administración de servicios** .  Una vez allí, consulte los siguientes pasos o vea el siguiente vídeo.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Cómo administrar suscripciones de nube de Visual Studio para los clientes

1. Inicie sesión en el [Centro de partners de Microsoft](https://partnercenter.microsoft.com).
0. Elija **Clientes** y el nombre del cliente.
0. Seleccione **Administración de servicios** .
0. Elija **Administrar suscripciones de Visual Studio** .

Si tiene más de una suscripción de Azure con este cliente, use el menú desplegable para elegir aquella con la que haya realizado las compras.  En **Resumen de licencias** se muestra el número de suscripciones que hay asignadas y cuántas de ellas están disponibles para cada opción de suscripción de nube de Visual Studio.  A través de este resumen también se pueden adquirir más suscripciones o reducir el número de suscripciones.

Seleccione **Agregar** para asignar una suscripción a un usuario nuevo.  El número en pantalla se actualiza y el usuario final recibe una notificación por correo electrónico. Tras esto, el usuario final puede iniciar sesión con la dirección de correo electrónico que proporcionó para activar la suscripción de Visual Studio en el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Para reasignar una suscripción de Visual Studio a otro usuario, puede eliminar el suscriptor actual y agregar uno nuevo.

Si un suscriptor no ha activado su suscripción de Visual Studio, puede deberse a que no haya recibido el correo electrónico de invitación.  Puede solicitar que se reenvíe la invitación de activación al usuario también desde el portal de administración de Visual Studio.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Ver precios de Visual Studio para partners CSP
Para ver los precios de Visual Studio para partners CSP, inicie sesión en el [Centro de partners](https://partnercenter.microsoft.com).  Elija **Precios y ofertas** a la izquierda.  Elija el archivo de precios del mes en curso en **servicios basados en el uso** , en la esquina superior derecha. Cuando se descargue la hoja de cálculo de Excel, vaya a la hoja **Lista de precios de Azure** y filtre la columna **Categoría de medición** por **Visual Studio** .

Así es como hay que interpretar lo que aparece en esta hoja de cálculo:

| Meter category    |   NOMBRE                 |  Unidades                                |           Qué es                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Programa para la mejora     | Empresa             |  Suscripción                         | Suscripción mensual de Visual Studio Enterprise   |
| Programa para la mejora     | Profesional           |  Suscripción                         | Suscripción mensual de Visual Studio Professional |

Ofrecemos un descuento del 5 % por la sexta unidad que se adquiera (para un mismo cliente) cada mes de cada suscripción de Visual Studio. Es por eso que aparecen dos filas por cada opción de suscripción. Una fila muestra un "valor mínimo" de 0, lo que debe interpretarse como el precio base de las primeras cinco unidades. La otra fila muestra un "valor mínimo" de 5, por lo que este es el precio con el 5 % de descuento que se aplica desde la sexta unidad en adelante.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>P: ¿Cómo se procesan los cargos de las suscripciones de nube **mensuales** ?
R: En la primera compra, facturaremos una cantidad prorrateada para cubrir los días restantes del mes actual. Por ejemplo, si se compran 10 suscripciones de nube mensuales de Visual Studio Professional el 15 de abril, cobraríamos solo cinco unidades (porque siguen quedando por delante 15 de los 30 días del mes en curso), o bien el 50 % y prorratearíamos las unidades facturadas al 50 %. A partir del 1 de mayo, y así cada mes en adelante hasta que se cancele, se facturarán las 10 unidades por completo.

Si, más adelante, la cantidad de pago se incrementa, también prorratearemos la diferencia en las unidades para cubrir los días restantes del mes en curso. Así, si el 10 de mayo se adquiere una suscripción de nube de Visual Studio Professional mensual más, facturaríamos aproximadamente 0,677 unidades (21 días restantes del mes de mayo, que tiene 31 días).

### <a name="q-how-do-cancellations-work"></a>P: ¿Cómo funcionan las cancelaciones?
R: Cuando una suscripción de nube de Visual Studio se cancela, se cancela la renovación automática. La suscripción prosigue hasta la fecha de renovación normal y, tras ello, sencillamente expira. Al expirar, el suscriptor de Visual Studio ya no puede usar Visual Studio ni disfrutar de ninguna otra ventaja de la suscripción.

En las suscripciones de nube mensuales, las cancelaciones surten efecto el primer día del siguiente mes. Si cancela solo algunas de las suscripciones de nube mensuales del cliente, asegúrese de quitar a los usuarios correspondientes al inicio del siguiente mes para, de este modo, procurar que las personas adecuadas sigan teniendo suscripciones activas asignadas.

En el caso de las suscripciones de nube anuales, las cancelaciones surten efecto el primer día del mes siguiente a los 12 meses desde la compra original, o 12 meses a partir del último cargo de renovación anual. Por ejemplo, si se ha adquirido una suscripción de nube anual de Visual Studio Enterprise el 3 de enero de 2018, permanecerá activa hasta el 1 de febrero de 2019, momento en el que se renueva automáticamente otro año. Si se cancela en cualquier momento desde entonces hasta el 1 de febrero de 2020, la suscripción caducará el 1 de febrero de 2020. No existe derecho de reembolso si una suscripción de nube anual se cancela en algún momento durante el año de vigencia de la suscripción.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>P: ¿Qué tipo de descuentos por volumen están disponibles para las suscripciones de Visual Studio?
R:  Disfrutará de un 5 % de descuento a partir de la sexta suscripción y en todas las siguientes *dentro del mismo tipo* de suscripción:
- Visual Studio Professional mensual
- Visual Studio Enterprise mensual

Por ejemplo, si se adquieren 6 suscripciones mensuales de Visual Studio Professional y 5 suscripciones mensuales de Visual Studio Enterprise, se pagará el precio normal de cinco suscripciones de Professional y se descontará un 5 % de la sexta, mientras que se abonará el precio normal de las cinco suscripciones de Enterprise.

Además, el descuento solo es válido en los cargos de un determinado período de facturación mensual. Es decir, si se adquieren 5 suscripciones anuales de Visual Studio Professional en un mes y el siguiente mes se adquieren otras 5 más, pagará el precio normal de las diez suscripciones.

Estos descuentos aparecen reflejados en los datos de precios del [Centro de partners](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>P: ¿Hay descuentos por renovación?
R:  No, los precios de las suscripciones de Visual Studio son fijos. El precio es el mismo tanto para las suscripciones nuevas como para las que sigan renovándose.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>P: ¿Existen opciones de precios de desarrollo/pruebas de Azure para CSP?
R: No en este momento. Los clientes pueden sacar partido de las ventajas de [precios de desarrollo y pruebas de Azure](https://azure.microsoft.com/pricing/dev-test/), pero no tenemos algo que sea específico para CSP.

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Vea las [preguntas más frecuentes sobre facturación en la nube](vscloud-billing-faq.md) para obtener respuestas a cuestiones habituales sobre la facturación.