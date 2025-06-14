# 🎲 抽奖开奖完整指南

## 🎯 开奖方式

### **方法一：管理员手动开奖（推荐）**

1. **创建抽奖**
   ```
   [lottery title="新年大抽奖" prize="iPhone 15 Pro" cost="50" max="100"]
   ```

2. **等待用户参与**
   - 用户点击"参与抽奖"按钮
   - 系统扣除积分并记录参与

3. **管理员开奖**
   - 管理员在抽奖帖子中会看到红色的"开奖"按钮
   - 点击"开奖"按钮
   - 确认开奖（显示参与人数）
   - 系统随机选择获奖者
   - 显示获奖者信息

### **方法二：API 开奖（高级用户）**

管理员可以通过 API 直接开奖：

```bash
# 开奖
curl -X POST "/lottery_plugin/admin/draw/[抽奖ID]" \
  -H "X-CSRF-Token: [TOKEN]" \
  -H "Content-Type: application/json"

# 查看抽奖状态
curl -X GET "/lottery_plugin/admin/status/[抽奖ID]"

# 取消抽奖
curl -X POST "/lottery_plugin/admin/cancel/[抽奖ID]" \
  -H "X-CSRF-Token: [TOKEN]"
```

## 🎮 完整使用流程

### **1. 创建抽奖**
管理员或有权限的用户在帖子中输入：
```
🎉 新年特别抽奖活动！

[lottery title="新年大奖" prize="MacBook Pro + iPhone 15" cost="100" max="50"]

奖品丰厚，欢迎参与！
```

### **2. 用户参与阶段**
- ✅ 用户看到抽奖框
- ✅ 显示奖品、积分消耗、参与人数
- ✅ 用户点击"参与抽奖"按钮
- ✅ 系统扣除积分并记录参与
- ✅ 更新参与人数显示

### **3. 开奖阶段**
- ✅ 管理员看到"开奖"按钮（红色）
- ✅ 点击开奖按钮
- ✅ 确认对话框：显示参与人数
- ✅ 系统随机选择获奖者
- ✅ 显示获奖者信息
- ✅ 抽奖状态变为"已完成"

## 🎯 抽奖状态说明

### **active（活跃）**
- 用户可以参与
- 显示"参与抽奖"按钮
- 管理员可以看到"开奖"按钮（有参与者时）

### **completed（已完成）**
- 显示获奖者信息
- 不能再参与
- 不显示任何操作按钮

### **cancelled（已取消）**
- 显示"抽奖已取消"
- 不能参与或开奖

## 🔧 管理员功能

### **开奖权限**
- 只有管理员可以开奖
- 必须有参与者才能开奖
- 每个抽奖只能开奖一次

### **开奖条件**
- ✅ 抽奖状态为"活跃"
- ✅ 至少有一个参与者
- ✅ 当前用户是管理员

### **开奖结果**
- 🎯 随机选择一个参与者作为获奖者
- 📝 记录开奖时间
- 🔄 更新抽奖状态为"已完成"
- 📢 显示获奖者信息

## 📋 界面显示

### **参与阶段界面**
```
┌─────────────────────────────────────┐
│ 🎉 新年大奖                         │
│                                     │
│ 奖品: MacBook Pro + iPhone 15       │
│ 参与人数: 25/50 (剩余 25 名额)      │
│ 消耗: 100 积分                      │
│                                     │
│ [参与抽奖 (100 积分)] [开奖]        │
│                                     │
└─────────────────────────────────────┘
```

### **开奖后界面**
```
┌─────────────────────────────────────┐
│ 🎉 新年大奖                         │
│                                     │
│ 奖品: MacBook Pro + iPhone 15       │
│ 参与人数: 50/50                     │
│ 消耗: 100 积分                      │
│                                     │
│ 🎉 恭喜 @username 获奖！            │
│                                     │
│ 开奖已完成                          │
└─────────────────────────────────────┘
```

## ⚠️ 注意事项

### **开奖前检查**
1. 确认参与人数合理
2. 检查抽奖设置是否正确
3. 确保有足够的参与者

### **开奖后处理**
1. 联系获奖者安排奖品发放
2. 可以在帖子中回复获奖者信息
3. 记录奖品发放状态

### **常见问题**
- **Q: 可以重新开奖吗？**
  A: 不可以，每个抽奖只能开奖一次

- **Q: 可以取消已开奖的抽奖吗？**
  A: 不可以，只能取消未开奖的抽奖

- **Q: 获奖者如何知道中奖？**
  A: 目前显示在抽奖框中，后续可以添加私信通知功能

## 🚀 高级功能（计划中）

- 📧 自动通知获奖者
- ⏰ 定时自动开奖
- 📊 抽奖统计报告
- 🎁 多奖品抽奖
- 📱 移动端优化

---

🎉 **现在您可以完整地创建和管理抽奖活动了！**
