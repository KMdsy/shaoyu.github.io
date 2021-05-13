# 1. 时空数据多指标预测

时空数据哪有几种
- 图片+时间轴
- 时间序列+空域关系

### Related Work

![da83bb35b2ee1661e1c9a674721a092](https://user-images.githubusercontent.com/16149619/118065808-2e857600-b3d0-11eb-9d1b-90659d92c37f.png)
![2afb0700c4e39369712fbb8ea34e0aa](https://user-images.githubusercontent.com/16149619/118066874-11ea3d80-b3d2-11eb-8fc6-d193e9e90d1b.png)
![092efde5fcc1ead4c548ea92808792d](https://user-images.githubusercontent.com/16149619/118066884-157dc480-b3d2-11eb-868b-6971c9d0cc3d.png)
![482d0beee98602dae12b360f6031d18](https://user-images.githubusercontent.com/16149619/118066889-17478800-b3d2-11eb-9cc5-158e6496540c.png)
![3e27d036423732fd15c7a62c1e1128c](https://user-images.githubusercontent.com/16149619/118066898-1a427880-b3d2-11eb-96a2-1bd2a807d5c7.png)
![58898959d166daba42e0ebb387b2f79](https://user-images.githubusercontent.com/16149619/118066914-20385980-b3d2-11eb-8019-9a7e6e2cb35f.png)
![dd47545c4bd922d7b84c960ee7d4833](https://user-images.githubusercontent.com/16149619/118066921-23cbe080-b3d2-11eb-8f48-6659212f580f.png)
![88c7451c8cc1e57e4d2eeb486c469df](https://user-images.githubusercontent.com/16149619/118066931-262e3a80-b3d2-11eb-9cbc-996f792bb8c6.png)
![30d0135c1f07ed84151f625d3d57a2e](https://user-images.githubusercontent.com/16149619/118066951-2cbcb200-b3d2-11eb-923e-83d27bd4d36e.png)
![6930d622e79c8636b9190138728649b](https://user-images.githubusercontent.com/16149619/118066956-2fb7a280-b3d2-11eb-83b6-b15bbc07d8d8.png)

### 数据集
![2b64a3575b3878a9420d6f72c5b7f68](https://user-images.githubusercontent.com/16149619/118065786-2594a480-b3d0-11eb-9c39-f4690cc4673a.png)

### 挑战

1. node edge均有异质性：

  + node：基站业务不同，数据分布不同
  + edge：node间有不同的关系（举例：来向与去向的高铁节点、小区间的节点）
 
![87bc8f9f29b296c3f76e60b2802642e](https://user-images.githubusercontent.com/16149619/118066346-24b04280-b3d1-11eb-920d-04e16840a234.png)

2. 缺乏连续性的假设：用户接入不受物理空间约束，可以瞬间从小区A接入到小区B

3. 突发性

![2e14a03c01af3b1caf0a662ee8a7146](https://user-images.githubusercontent.com/16149619/118066497-6b05a180-b3d1-11eb-9629-c2f33b294cfa.png)

4. 网络结构复杂性（领区关系）：不同区域，基站之间的连接密集程度有很大不同

![175124e6e9fd50b498402605498cb46](https://user-images.githubusercontent.com/16149619/118066700-c041b300-b3d1-11eb-832e-d075536509e7.png)


### 自己的工作

强调自适应感受野，强调异质性

![70fcdc172c8cedf6935d33ac839464a](https://user-images.githubusercontent.com/16149619/118066996-43630900-b3d2-11eb-985d-f46dcef6ef33.png)
![37a65aed9e33e8fa09b12b8be7683c6](https://user-images.githubusercontent.com/16149619/118066999-452ccc80-b3d2-11eb-8d9a-12dc0f79a6d1.png)
![02bb2f207040d2afe6de2757b8c1e72](https://user-images.githubusercontent.com/16149619/118067004-46f69000-b3d2-11eb-84cb-9d979621749f.png)
![a0a14ff67f978b4ad952b64ff14c559](https://user-images.githubusercontent.com/16149619/118067008-4958ea00-b3d2-11eb-9f61-2ccde47c3644.png)
![c16290875c6b0455c241f091633377a](https://user-images.githubusercontent.com/16149619/118067012-4bbb4400-b3d2-11eb-9e42-491317cf8528.png)

-----------

# 2. 人机物融合智能运维：感知、诊断、交互

重点：需要融合人类知识到已有的时间序列、日志分析中

![17bde0bb13da6f7b437d75aefb74218](https://user-images.githubusercontent.com/16149619/118067350-ef0c5900-b3d2-11eb-9899-4b577997d00c.png)

主要分析日志数据，数据特点：半结构化、多言且复杂、不同组件、第三方组件日志的异质性。

### 难点

![83e9edce68a0e8f224e3abf3e4536c4](https://user-images.githubusercontent.com/16149619/118067374-00edfc00-b3d3-11eb-8e6d-938d3f9183cf.png)
![ba672144e6d23c3ab8da3696835ddc1](https://user-images.githubusercontent.com/16149619/118067397-0ba89100-b3d3-11eb-8e92-cc80bb72edc6.png)

### 分布式系统的特点

分布式系统，统一请求日志在数据中交替出现，而不唯一

...

![29fb6e68dc5cf6736622b00546c8985](https://user-images.githubusercontent.com/16149619/118067606-7b1e8080-b3d3-11eb-85db-c757c38269b5.png)

### 他们的工作

概述

![e09e7e6521aabee6c58e6aa477b81cb](https://user-images.githubusercontent.com/16149619/118067701-a7d29800-b3d3-11eb-9f81-b0095b575551.png)

重点1：模型适应性问题，自学习、自更新的故障预测模型，human-in-loop

![5f23f647ca6efef99e4caa69ee2a015](https://user-images.githubusercontent.com/16149619/118067887-0435b780-b3d4-11eb-8890-a73e3d0bfbd9.png)

重点2：机器学习结果如何提高人类的运维水平，指导程序员设置meaningful的日志打印点（打印点越多，日志包含的信息越无用），实际效果大幅减少打印点、且提升了故障诊断准确度

![f2b06778d60907994e463c2649ea753](https://user-images.githubusercontent.com/16149619/118068263-a6559f80-b3d4-11eb-9f93-9b2df53c2550.png)

重点3：CMDB相关

![43bd7aa2f12acc7183ce089ab7d53f4](https://user-images.githubusercontent.com/16149619/118068466-fcc2de00-b3d4-11eb-80f5-4841c766391b.png)
![24f3046d112f0daa16561614fad677a](https://user-images.githubusercontent.com/16149619/118068476-ffbdce80-b3d4-11eb-9c3d-6226fc2896b7.png)
![91c0926c0db9d0e85064f0f944e80e7](https://user-images.githubusercontent.com/16149619/118068633-47445a80-b3d5-11eb-8892-8ab0c02406f6.png)

重点4：知识图图谱

![2b060c89fc58c019e5d86588c8b2410](https://user-images.githubusercontent.com/16149619/118069018-fa14b880-b3d5-11eb-87c1-6b59a87d22fc.png)
![cbef862f03ea4a8d74de16e561aa09f](https://user-images.githubusercontent.com/16149619/118069021-fb45e580-b3d5-11eb-9d98-8ffae06434f9.png)

重点5：人机智能问答

![f9b1bd79a7e34528ad30ea964f2116b](https://user-images.githubusercontent.com/16149619/118069086-1b75a480-b3d6-11eb-8f15-74ab2a01f95b.png)
![ACL2020_8dbe96fbf771796f37977008d26fc1e](https://user-images.githubusercontent.com/16149619/118069207-57106e80-b3d6-11eb-9748-0aba1fa8a83a.png)
![IJCAI2020_668cd8dcc538e660acd07ea56ffa7c2](https://user-images.githubusercontent.com/16149619/118069295-82935900-b3d6-11eb-9319-4233679d332c.png)


------------

# 3. 落地经验

![b307dd866403412e2fe07928660b09e](https://user-images.githubusercontent.com/16149619/118069658-1f55f680-b3d7-11eb-9743-cbf86997616e.png)









