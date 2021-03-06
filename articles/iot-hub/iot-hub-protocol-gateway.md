---
title: Puerta de enlace de protocolos de IoT de Azure | Microsoft Docs
description: "Describe cómo usar una puerta de enlace de protocolo de IoT de Azure para extender el protocolo y las funcionalidades de IoT Hub para permitir que los dispositivos se conecten al centro que usa los protocolos no compatibles con IoT de forma nativa."
services: iot-hub
documentationcenter: 
author: kdotchkoff
manager: timlt
editor: 
ms.assetid: 555e59ae-3136-4533-8ba8-f3a3b6acf648
ms.service: iot-hub
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/23/2016
ms.author: kdotchko
translationtype: Human Translation
ms.sourcegitcommit: e223d0613cd48994315451da87e6b7066585bdb6
ms.openlocfilehash: 17250760526e72c05ee178e235a57082e2dfff94


---
# <a name="support-additional-protocols-for-iot-hub"></a>Compatibilidad con protocolos adicionales para centro de IoT Hub
IoT Hub de Azure admite de forma nativa la comunicación a través de los protocolos MQTT, AMQP y HTTP. En algunos casos, puede que los dispositivos o las puertas de enlace de campo no puedan usar uno de estos protocolos estándar y requerirán la adaptación del mismo. En esos casos, puede usar una puerta de enlace personalizada. Una puerta de enlace personalizada puede habilitar la adaptación de protocolos para los extremos del Centro de IoT reduciendo el tráfico que se origina o finaliza en el Centro de IoT. Puede usar la [Puerta de enlace de protocolos de IoT de Azure](https://github.com/Azure/azure-iot-protocol-gateway/blob/master/README.md) como puerta de enlace personalizada para permitir la adaptación de protocolos para el Centro de IoT.

## <a name="azure-iot-protocol-gateway"></a>Puerta de enlace de protocolos de IoT de Azure
La puerta de enlace de protocolos de IoT de Azure es un marco para la adaptación de protocolos diseñado para la comunicación bidireccional a gran escala de dispositivos con el Centro de IoT. La puerta de enlace de protocolo es un componente de acceso directo que acepta conexiones de dispositivos a través de un protocolo específico. Une el tráfico al Centro de IoT sobre AMQP 1.0. La puerta de enlace de protocolo de IoT de Azure está disponible como proyecto de software de código abierto para ofrecer flexibilidad para agregar compatibilidad con una variedad de protocolos y versiones de protocolo.

Puede implementar la puerta de enlace de protocolos en Azure de una manera altamente escalable con roles de trabajo de Servicios en la nube de Azure. Además, la puerta de enlace de protocolos puede implementarse en entornos locales como puertas de enlace de campo.

La puerta de enlace de protocolos de IoT de Azure incluye un adaptador de protocolos de MQTT que le permite personalizar el comportamiento del protocolo de MQTT si es necesario. Puesto que IoT Hub proporciona compatibilidad integrada para el protocolo de MQTT v3.1.1, solo puede utilizar el adaptador de protocolo MQTT si necesita personalizaciones de protocolo o requisitos específicos para una funcionalidad adicional.

El adaptador de MQTT también muestra el modelo de programación para la creación de adaptadores de protocolo para otros protocolos. Además, el modelo de programación de puerta de enlace de protocolo de IoT de Azure le permite conectar componentes personalizados para su procesamiento especializado como, por ejemplo, autenticación personalizada, transformaciones de mensajes, compresión y descompresión o cifrado y descifrado de tráfico entre los dispositivos y el IoT Hub.

Para mayor flexibilidad, la puerta de enlace de protocolos y la implementación de MQTT se ofrecen como proyecto de software de código abierto. Esto le permite personalizar la implementación según sea necesario.

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre la puerta de enlace de protocolos de IoT de Azure y cómo usarlo e implementarlo como parte de su solución de IoT, vea:

* [Repositorio de puerta de enlace de protocolos de IoT de Azure en GitHub](https://github.com/Azure/azure-iot-protocol-gateway/blob/master/README.md)
* [Guía para desarrolladores de puerta de enlace de protocolos de IoT de Azure](https://github.com/Azure/azure-iot-protocol-gateway/blob/master/docs/DeveloperGuide.md)

Para más información acerca de planificación de la implementación del Centro de IoT, consulte:

* [Comparación con Event Hubs][lnk-compare]
* [Escalado, alta disponibilidad y recuperación ante desastres][lnk-scaling]

Para explorar aún más las funcionalidades de Centro de IoT, consulte:

* [Guía para desarrolladores de IoT Hub][lnk-devguide]
* [Simulación de un dispositivo con el SDK de puerta de enlace de IoT][lnk-gateway]

[lnk-compare]: iot-hub-compare-event-hubs.md
[lnk-scaling]: iot-hub-scaling.md
[lnk-devguide]: iot-hub-devguide.md
[lnk-gateway]: iot-hub-linux-gateway-sdk-simulated-device.md



<!--HONumber=Dec16_HO1-->


