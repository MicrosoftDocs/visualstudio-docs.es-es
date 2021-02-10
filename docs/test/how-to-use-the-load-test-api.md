---
title: API de pruebas de carga
description: Aprenda a usar la API de pruebas de carga, la cual admite complementos de prueba que pueden controlar o mejorar una prueba de carga.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 281e64f83766b6b42dd9f076726c429c9432245b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879558"
---
# <a name="how-to-use-the-load-test-api"></a>Cómo: Usar la API de pruebas de carga

Visual Studio admite complementos de pruebas de carga que puedan controlar o mejorar una prueba de carga. Los complementos de pruebas de carga son clases definidas por el usuario que implementan la interfaz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> situada en el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Los complementos de pruebas de carga permiten un control personalizado de las pruebas de carga, por ejemplo, para anular una prueba de carga cuando se alcanza un valor de contador o un umbral de error. Utilice las propiedades de la clase <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> para obtener o establecer parámetros de prueba de carga a partir del código definido por el usuario. Utilice los eventos de la clase <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> para asociar delegados para notificaciones cuando la prueba de carga se esté ejecutando.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> El Examinador de objetos se usa para examinar el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.LoadTesting>. Los editores de Visual C# y de Visual Basic ofrecen compatibilidad con IntelliSense para codificar con las clases del espacio de nombres.

También se pueden crear complementos para pruebas de rendimiento web. Para obtener más información, vea [Cómo: Crear un complemento de pruebas de rendimiento web](../test/how-to-create-a-web-performance-test-plug-in.md) y [Cómo: Crear un complemento de nivel de solicitud](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Para usar el espacio de nombres LoadTesting

1. Abra un proyecto de prueba de carga y rendimiento web que contenga una prueba de carga.

2. Agregue un proyecto de biblioteca de clases de Visual C# o Visual Basic a la solución de prueba.

3. Agregue una referencia en el proyecto de prueba de carga y rendimiento web para el proyecto de biblioteca de clases.

4. Agregue una referencia a la DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework en el proyecto Biblioteca de clases.

5. En el archivo de clase ubicado en el proyecto de biblioteca de clases, agregue una instrucción `using` para el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

6. Cree una nueva clase pública que implemente la interfaz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

7. Compile el proyecto.

8. Agregue el nuevo complemento de prueba de carga mediante el Editor de prueba de carga:

    1. Haga clic con el botón derecho en el nodo raíz de la prueba de carga y, luego, elija **Agregar complemento de prueba de carga**.

    2. Aparecerá el cuadro de diálogo **Agregar complemento de prueba de carga**.

    3. En el panel **Propiedades del complemento seleccionado**, establezca los valores iniciales que el complemento va a usar en tiempo de ejecución.

        > [!NOTE]
        > Puede exponer tantas propiedades como desee de sus complementos. Basta con hacerlas públicas, que se puedan establecer y que tengan un tipo base como Integer, Boolean o String. También puede editar las propiedades del complemento de pruebas de carga posteriormente desde la ventana **Propiedades**.

9. Ejecute la prueba de carga.

     Para obtener una implementación de <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, vea [Cómo: Crear un complemento de prueba de carga](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Cómo: Usar la API de prueba de rendimiento web](../test/how-to-use-the-web-performance-test-api.md)
- [Cómo: Crear un complemento de prueba de carga](../test/how-to-create-a-load-test-plug-in.md)
