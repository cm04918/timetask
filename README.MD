# 轮询任务会出现错误...会建立很多副本，等有空修改！！！！！！！！！！



此插件需通过godcmd管理员认证后方可启用，以确保只有授权用户能够创建定时任务，从而维护系统的安全性和专业性。
在原有插件的基础上，我们进行了以下功能优化：新增了【延时功能】，允许用户根据需要设置不同的执行时间；以及【用户指定功能】，使用户能够自定义任务参数，以满足更多样化的需求。

时间会进位，比如建立8:00的任务，延时1-60分钟，如随机是60分钟，就会9:00发送，那么有一个问题，23点后的任务，你们看着办，这个没做日期优化处理。

优化原因：原版限制了向个人发送信息的灵活性，且总是定时在8:00发送，显得过于机械和缺乏人情味。为了增添人性化元素，我们引入了延时服务功能，以提供更加灵活和个性化的沟通体验。

# timetask
一款支持自定义定时任务的chatgpt-on-wechat插件，支持自定义时间、轮询周期、自定义时间，包含动态添加任务、取消任务、查看任务列表等功能，一款定时任务系统的插件。
路径和原版一样“/plugins/timetask”没修改。


timetask原版使用方法见：https://github.com/haikerapples/timetask


延时功能：通过 t[min-max] 指定任务在设定的时间范围内随机延时执行。
用户指定功能：通过 user[用户名] 或 group[群标题] 指定任务发送给特定的用户或群组。
结合使用：延时功能和用户指定功能可以结合使用，实现更灵活的任务调度。



## **【延时功能】**

延时功能允许用户在添加定时任务时，指定任务在设定的时间范围内随机延时执行。这对于需要避免任务过于集中执行的场景非常有用。

### **使用方式**

在添加定时任务时，可以在事件后面添加 `t[延时范围]`，表示任务将在指定的时间范围内随机延时执行。延时范围格式为 `min-max`，单位为分钟。

#### **示例**

1. **延时任务**：
   ```
   $time 每天 10:00 提醒我健身 t[3-5]
   ```
   - 解释：任务将在每天 10:00 之后的 3 到 5 分钟内随机执行。

2. **延时任务结合拓展功能**：
   ```
   $time 每周三 10:30 早报 t[1-2]
   ```
   - 解释：任务将在每周三 10:30 之后的 1 到 2 分钟内随机执行，并发送早报。

3. **延时任务结合群任务**：
   ```
   $time 每天 09:00 提醒我开会 group[工作群] t[5-10]
   ```
   - 解释：任务将在每天 09:00 之后的 5 到 10 分钟内随机执行，并在指定的群中发送提醒。

### **注意事项**

- 延时功能仅适用于单次任务，轮询任务（如每天、每周等）不支持延时。
- 延时时间范围为 `min-max`，且 `min` 必须小于 `max`。
- 延时功能不会影响任务的周期设定，任务仍会在设定的周期内执行。

---

## **【用户指定功能】**

用户指定功能允许用户在添加定时任务时，指定任务发送给特定的用户或群组。这对于需要将任务定向发送给某个用户或群组的场景非常有用。

### **使用方式**

在添加定时任务时，可以在事件后面添加 `user[用户名]` 或 `group[群标题]`，表示任务将发送给指定的用户或群组。

#### **示例**

1. **指定用户任务**：
   ```
   $time 每天 08:00 提醒我吃早餐 user[张三]
   ```
   - 解释：任务将在每天 08:00 执行，并发送给用户名为 `张三` 的用户。

2. **指定群组任务**：
   ```
   $time 每周五 18:00 提醒我开会 group[工作群]
   ```
   - 解释：任务将在每周五 18:00 执行，并发送给群标题为 `工作群` 的群组。

3. **结合延时功能**：
   ```
   $time 每天 12:00 提醒我吃饭 user[李四] t[2-4]
   ```
   - 解释：任务将在每天 12:00 之后的 2 到 4 分钟内随机执行，并发送给用户名为 `李四` 的用户。

### **注意事项**

- 指定的用户名或群标题必须准确，且机器人必须在该群组中或与指定用户是好友关系。
- 如果指定的用户或群组不存在，任务将无法执行，并会提示错误信息。
- 用户指定功能可以与延时功能结合使用，实现更灵活的任务调度。

---

## **【综合示例】**

以下是一个结合延时功能和用户指定功能的综合示例：

```
$time 每天 09:00 提醒我开会 group[工作群] t[5-10]
```

- **解释**：
  - 任务将在每天 09:00 之后的 5 到 10 分钟内随机执行。
  - 任务将发送给群标题为 `工作群` 的群组。

---

## **【总结】**

- **延时功能**：通过 `t[min-max]` 指定任务在设定的时间范围内随机延时执行。
- **用户指定功能**：通过 `user[用户名]` 或 `group[群标题]` 指定任务发送给特定的用户或群组。
- **结合使用**：延时功能和用户指定功能可以结合使用，实现更灵活的任务调度。

通过这些功能，用户可以更精确地控制任务的执行时间和接收对象，满足多样化的需求。

---

