---
title: 'Cómo: cambiar el espacio de nombres de un lenguaje específico de dominio'
description: Proporciona información sobre cómo cambiar el espacio de nombres de un lenguaje específico de dominio.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: a7b0de26fdc1a7982347a12c283a6aa73e9aad12
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809445"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Cómo: cambiar el espacio de nombres de un lenguaje específico de dominio

Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Realice el cambio en el **Explorador de DSL**, en las propiedades del proyecto de paquete DSL y en la información de ensamblado.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1. En el **Explorador de DSL**, seleccione el nodo **DSL** .

2. En la ventana **propiedades** , cambie la propiedad **espacio de nombres** .

3. Guarde la solución y transforme las plantillas.

4. En el menú **proyecto** , elija **propiedades de DSL**.

   Aparecen las propiedades del proyecto.

5. Seleccione la pestaña **Aplicación**.

6. Cambie la propiedad **espacio de nombres predeterminado** al nuevo nombre del espacio de nombres.

7. Si también desea cambiar el nombre del ensamblado, cambie la **propiedad nombre del ensamblado.**

8. Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito código personalizado, asegúrese de cambiar las referencias de espacio de nombres y clase en los archivos de código.

10. Restablezca la instancia experimental de Visual Studio.

    1. Elimine ** \\ \Users**_{su nombre}_**\AppData\Local\Microsoft\VisualStudio \\ \* exp**.

    2. En el menú **Inicio** de Windows, elija **todos los programas**  >  **Microsoft Visual Studio 2010**  >  **herramientas**  >  **del SDK restablecer la instancia experimental**.

11. En el menú **compilar** , elija **recompilar solución**.

## <a name="see-also"></a>Consulte también

[Glosario de herramientas de lenguajes específicos de dominio](/previous-versions/bb126564(v=vs.100))