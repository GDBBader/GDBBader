---

title: BPMN 格式
date: 2023-02-09 21:56
tags: [BPMN,bpmn-js,xml]

---
bpmn格式
有结点
有坐标

<!--more-->

bpmn-js导出文件
```xml
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions 
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" 
  xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" 
  xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" 
  xmlns:di="http://www.omg.org/spec/DD/20100524/DI" 
  id="Definitions_1da3685" 
  targetNamespace="http://bpmn.io/schema/bpmn" 
  exporter="bpmn-js (https://demo.bpmn.io)" 
  exporterVersion="11.1.0">
  <bpmn:process id="Process_1e0e6vm" isExecutable="false">
    <bpmn:startEvent id="StartEvent_1y21hlj">
      <bpmn:outgoing>Flow_10al3v7</bpmn:outgoing>
    </bpmn:startEvent>
    <bpmn:exclusiveGateway id="Gateway_1f7za4t">
      <bpmn:incoming>Flow_10al3v7</bpmn:incoming>
      <bpmn:outgoing>Flow_1hlmrst</bpmn:outgoing>
    </bpmn:exclusiveGateway>
    <bpmn:task id="Activity_0vfyrvg">
      <bpmn:incoming>Flow_1hlmrst</bpmn:incoming>
      <bpmn:outgoing>Flow_0uc4kaj</bpmn:outgoing>
    </bpmn:task>
    <bpmn:sequenceFlow id="Flow_10al3v7" sourceRef="StartEvent_1y21hlj" targetRef="Gateway_1f7za4t" />
    <bpmn:sequenceFlow id="Flow_1hlmrst" sourceRef="Gateway_1f7za4t" targetRef="Activity_0vfyrvg" />
    <bpmn:intermediateThrowEvent id="Event_1xctbtr">
      <bpmn:incoming>Flow_0uc4kaj</bpmn:incoming>
    </bpmn:intermediateThrowEvent>
    <bpmn:sequenceFlow id="Flow_0uc4kaj" sourceRef="Activity_0vfyrvg" targetRef="Event_1xctbtr" />
  </bpmn:process>
  <bpmndi:BPMNDiagram id="BPMNDiagram_1">
    <bpmndi:BPMNPlane id="BPMNPlane_1" bpmnElement="Process_1e0e6vm">
      <bpmndi:BPMNShape id="_BPMNShape_StartEvent_2" bpmnElement="StartEvent_1y21hlj">
        <dc:Bounds x="156" y="82" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Gateway_1f7za4t_di" bpmnElement="Gateway_1f7za4t" isMarkerVisible="true">
        <dc:Bounds x="149" y="215" width="50" height="50" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Activity_0vfyrvg_di" bpmnElement="Activity_0vfyrvg">
        <dc:Bounds x="124" y="390" width="100" height="80" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNShape id="Event_1xctbtr_di" bpmnElement="Event_1xctbtr">
        <dc:Bounds x="156" y="552" width="36" height="36" />
      </bpmndi:BPMNShape>
      <bpmndi:BPMNEdge id="Flow_10al3v7_di" bpmnElement="Flow_10al3v7">
        <di:waypoint x="174" y="118" />
        <di:waypoint x="174" y="215" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_1hlmrst_di" bpmnElement="Flow_1hlmrst">
        <di:waypoint x="174" y="265" />
        <di:waypoint x="174" y="390" />
      </bpmndi:BPMNEdge>
      <bpmndi:BPMNEdge id="Flow_0uc4kaj_di" bpmnElement="Flow_0uc4kaj">
        <di:waypoint x="174" y="470" />
        <di:waypoint x="174" y="552" />
      </bpmndi:BPMNEdge>
    </bpmndi:BPMNPlane>
  </bpmndi:BPMNDiagram>
</bpmn:definitions>
```
bpm导出文件
```xml
<?xml version="1.0" encoding="UTF-8"?>
<bpmn:definitions 
xmi:version="2.0" 
xmlns:xmi="http://www.omg.org/XMI" 
xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
exporter="http://www.ibm.com/BPM" 
exporterVersion="8.6.3" 
id="bpmnid-d3932731-c84c-45b1-b5be-74fc6e8178f6" 
targetNamespace="http://H2606908-Pricing/Start/Print Bill">
  <bpmn:process id="bpmnid-ee27fabe-da1f-4b89-b549-245f1840c110" name="Print Bill" isClosed="false" processType="None">
    <bpmn:userTask id="bpmnid-0a7074e5-e562-49b6-a53d-444f58588955" name="Show Bill"/>
    <bpmn:userTask id="bpmnid-26d8dff1-3efe-4172-bb99-a9b2c9d2a389" name="Purchase an item"/>
    <bpmn:startEvent id="bpmnid-e9723ca6-c2a4-4f87-be46-23f8dddd36b6" name="Start"/>
    <bpmn:endEvent id="bpmnid-019bd523-1fd4-4d5e-aec9-0b5eb8f9b415" name="End"/>
    <bpmn:serviceTask id="bpmnid-a299d2fe-85d2-432a-9538-8b2b1243e588" name="Compute VAT">
      <bpmn:documentation textFormat="text/plain">Compute the value-added tax for some goods.</bpmn:documentation>
    </bpmn:serviceTask>
    <bpmn:sequenceFlow id="bpmnid-a535bbb2-0457-412e-bfea-129b7a4d698a" name="To Compute Bill" sourceRef="bpmnid-e9723ca6-c2a4-4f87-be46-23f8dddd36b6" targetRef="bpmnid-26d8dff1-3efe-4172-bb99-a9b2c9d2a389"/>
    <bpmn:sequenceFlow id="bpmnid-e447c15d-1d15-4f56-ad96-80ea7c2a5029" name="To Show Bill" sourceRef="bpmnid-a299d2fe-85d2-432a-9538-8b2b1243e588" targetRef="bpmnid-0a7074e5-e562-49b6-a53d-444f58588955"/>
    <bpmn:sequenceFlow id="bpmnid-37390972-01cc-45a2-8f66-14519a718def" name="To End" sourceRef="bpmnid-0a7074e5-e562-49b6-a53d-444f58588955" targetRef="bpmnid-019bd523-1fd4-4d5e-aec9-0b5eb8f9b415"/>
    <bpmn:sequenceFlow id="bpmnid-cd6bb92e-6e4a-4b8c-9108-f8466a4ba430" name="To Compute VAT" sourceRef="bpmnid-26d8dff1-3efe-4172-bb99-a9b2c9d2a389" targetRef="bpmnid-a299d2fe-85d2-432a-9538-8b2b1243e588"/>
  </bpmn:process>
</bpmn:definitions>

```
## 一、bpmn文件结构
## 1.1 `<?xml version="1.0" encoding="UTF-8"?>`
指定xml文件的编码格式。
## 1.2 `<bpmn:definitions>`
根元素，所有的BPMN文件都必须以此为根。
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092152073.png)

### 1.2.1 `<bpmn:sequenceFlow>`
顺序流，即从A指向B。
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092152102.png)
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092152764.png)
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092153224.png)

### 1.2.2 `<bpmn:incoming>、<bpmn:outgoing>`
从哪进，从哪出。![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092153391.png)
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092153958.png)

### 1.2.3 `<bpmndi:BPMNDiagram>`
描述BPMN模型的部分，大小、位置等。
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092153454.png)
为了渲染一个process，BPMN diagram元素是必要的。
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092154476.png)

## 二、bpm导出文件无法直接使用bpmn-js渲染的原因
报错信息
```
>bpmn-to-image "Print Bill.bpmn";o.png
failed to export diagram(s)
Error: Evaluation failed: Error: no diagram to display
```
[https://forum.camunda.io/t/no-diagram-to-display-why/14799/6](https://forum.camunda.io/t/no-diagram-to-display-why/14799/6)

[https://github.com/bpmn-io/bpmn-js/issues/853](https://github.com/bpmn-io/bpmn-js/issues/853)

bpmn-js作者话：

[https://github.com/bpmn-io/bpmn-js/issues/858#issuecomment-417922237](https://github.com/bpmn-io/bpmn-js/issues/858#issuecomment-417922237)

在缺少di的情况下，能否通过bpmn-js生成图片：

bpmn-js作者话：[https://github.com/bpmn-io/bpmn-js/issues/853#issuecomment-415155081](https://github.com/bpmn-io/bpmn-js/issues/853#issuecomment-415155081)

> Unfortunately layouting / generating the diagram DI is not a simple task.

![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302092154127.png)

解决方案
[https://github.com/camunda-consulting/migrate-to-camunda-tools](https://github.com/camunda-consulting/migrate-to-camunda-tools)
## 参考
1. [Migrating process BPMN from IBM BPM to Camunda](https://camunda.com/blog/2020/04/migrating-process-bpmn-from-ibm-bpm-to-camunda-step-by-step-tutorial/)