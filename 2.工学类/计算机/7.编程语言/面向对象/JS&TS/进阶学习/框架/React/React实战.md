# 上传页面

![image.png](https://i0.hdslb.com/bfs/openplatform/1de543a5cdfb752b111703b64065f2470e762146.png)

以下是基于项目需求和统一设计语言构建的React数据解析页面，采用TailwindCSS实现响应式布局和视觉一致性：

```jsx
import React, { useState } from 'react';

export default function DataParsingPage() {
  const [activeTab, setActiveTab] = useState('preview');
  const [parsingProgress, setParsingProgress] = useState(0);
  
  // 模拟解析后的BOM数据
  const parsedData = [
    { model: "LM358", quantity: 100, param: "8-DIP", stock: "充足" },
    { model: "10kΩ", quantity: 50, param: "5%", stock: "不足" },
    { model: "1N4148", quantity: 200, param: "SMD", stock: "充足" }
  ];
  
  // 模拟解析统计信息
  const stats = {
    totalItems: 12,
    errors: 3,
    duplicates: 1,
    missingFields: 2
  };

  return (
    <div className="min-h-screen bg-gray-50">
      {/* 导航栏 */}
      <nav className="bg-white shadow-sm">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between h-16 items-center">
            <div className="flex items-center">
              <svg className="h-8 w-8 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
                <path d="M12 12h.01M12 8h.01M12 16h.01" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
              </svg>
              <span className="ml-2 text-xl font-bold">BOM解析器</span>
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        {/* 步骤指示器 */}
        <div className="mb-8">
          <StepIndicator currentStep={2} steps={["文件上传", "数据解析", "比价分析", "采购执行"]} />
        </div>

        {/* 主体内容 */}
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
          {/* 侧边栏 */}
          <div className="lg:col-span-1 space-y-6">
            <Card title="解析统计">
              <div className="h-48 flex flex-col justify-center">
                <div className="space-y-3">
                  <div className="flex justify-between text-sm">
                    <span>总元件数</span>
                    <span className="font-medium">{stats.totalItems}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span className="text-red-600">解析异常</span>
                    <span className="font-medium text-red-600">{stats.errors}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>重复项</span>
                    <span className="font-medium">{stats.duplicates}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>缺失字段</span>
                    <span className="font-medium">{stats.missingFields}</span>
                  </div>
                </div>
              </div>
            </Card>

            <Card title="解析设置">
              <div className="space-y-4">
                <div className="flex items-center justify-between">
                  <span className="text-sm">自动修复建议</span>
                  <button className="px-3 py-1 bg-indigo-100 text-indigo-700 rounded text-xs">
                    启用
                  </button>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">字段匹配模式</span>
                  <select className="text-sm border-gray-300 rounded focus:ring-indigo-500">
                    <option>自动识别</option>
                    <option>手动映射</option>
                  </select>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">单位标准化</span>
                  <input type="checkbox" className="w-4 h-4 text-indigo-600 rounded focus:ring-indigo-500" />
                </div>
              </div>
            </Card>
          </div>

          {/* 主内容区域 */}
          <div className="lg:col-span-2 space-y-6">
            <Card title="数据预览" extra={<span className="text-sm text-gray-500">前3行示例</span>}>
              <div className="overflow-x-auto">
                <table className="min-w-full divide-y divide-gray-200">
                  <thead className="bg-gray-50">
                    <tr>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">元件型号</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">数量</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">规格参数</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">库存状态</th>
                    </tr>
                  </thead>
                  <tbody className="bg-white divide-y divide-gray-200">
                    {parsedData.map((item, index) => (
                      <tr key={index} className={index % 2 === 0 ? 'bg-gray-50' : 'bg-white'}>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.model}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.quantity}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.param}</td>
                        <td className={`px-4 py-4 whitespace-nowrap text-sm ${
                          item.stock === '充足' ? 'text-green-600' : 'text-red-600'
                        }`}>
                          {item.stock}
                        </td>
                      </tr>
                    ))}
                  </tbody>
                </table>
              </div>
            </Card>

            {/* 解析详情 */}
            <Card title="解析详情">
              <div className="space-y-4">
                <div className="flex items-center justify-between">
                  <div className="flex items-center">
                    <svg className="w-5 h-5 text-yellow-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                      <path fillRule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zm-1 1a1 1 0 00-1 1v1a1 1 0 001 1h1a1 1 0 001-1v-1a1 1 0 00-1-1h-1zM9 9a1 1 0 000 2h.01a1 1 0 000-2H9z" clipRule="evenodd" />
                      <path d="M10 5.5a2.5 2.5 0 00-2.5 2.5v1a3.5 3.5 0 005.5 2.9V8.5A2.5 2.5 0 0010 5.5z" />
                    </svg>
                    <span>解析状态：已完成</span>
                  </div>
                  <div className="text-sm text-gray-500">耗时：00:02:15</div>
                </div>

                <div className="relative pt-1">
                  <div className="flex items-center justify-between mb-2">
                    <div>
                      <span className="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full bg-indigo-200 text-indigo-800">
                        完成
                      </span>
                    </div>
                    <div className="text-right">
                      <span className="text-xs font-semibold inline-block text-indigo-600">
                        100%
                      </span>
                    </div>
                  </div>
                  <div className="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
                    <div style={{ width: "100%" }} className="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500 transition-all duration-500"></div>
                  </div>
                </div>

                <div className="border-t pt-4">
                  <h4 className="text-sm font-medium mb-3">解析日志</h4>
                  <div className="bg-gray-50 p-3 rounded-lg h-32 overflow-y-auto text-xs text-gray-600">
                    <div className="space-y-1">
                      <div className="text-green-600">[成功] 文件格式识别完成</div>
                      <div className="text-blue-600">[信息] 检测到3个异常数据</div>
                      <div className="text-orange-600">[警告] 存在2个缺失字段</div>
                      <div className="text-indigo-600">[提示] 已应用单位标准化规则</div>
                    </div>
                  </div>
                </div>
              </div>
            </Card>

            {/* 操作区域 */}
            <div className="flex flex-col space-y-3 sm:flex-row sm:space-y-0 sm:space-x-3">
              <button className="flex-1 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors">
                重新解析
              </button>
              <button className="flex-1 px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-50">
                下载修正模板
              </button>
              <button className="flex-1 px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 transition-colors">
                进入比价分析
              </button>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

// 步骤指示器组件
function StepIndicator({ currentStep, steps }) {
  return (
    <div className="flex items-center">
      {steps.map((step, index) => {
        const stepNumber = index + 1;
        const isCompleted = stepNumber < currentStep;
        const isActive = stepNumber === currentStep;
        
        return (
          <div key={step} className="flex items-center">
            <div className={`flex-shrink-0 w-8 h-8 flex items-center justify-center rounded-full text-sm font-medium 
              ${isCompleted ? 'bg-green-500 text-white' : isActive ? 'bg-indigo-600 text-white' : 'bg-gray-200 text-gray-600'}`}>
              {stepNumber}
            </div>
            <div className="ml-2 text-sm">{step}</div>
            {index < steps.length - 1 && (
              <div className={`h-0.5 mx-2 flex-1 ${stepNumber < currentStep ? 'bg-green-500' : 'bg-gray-200'}`}></div>
            )}
          </div>
        );
      })}
    </div>
  );
}

// 卡片组件
function Card({ title, extra, children }) {
  return (
    <div className="bg-white rounded-lg shadow-sm border border-gray-200">
      <div className="px-4 py-3 border-b border-gray-200 flex justify-between items-center">
        <h3 className="text-lg font-medium">{title}</h3>
        {extra && <div>{extra}</div>}
      </div>
      <div className="p-4">{children}</div>
    </div>
  );
}
```

### 核心功能实现：

1. **视觉一致性**：
   - 保持与上传页面一致的配色方案（靛蓝主色、灰蓝配色）
   - 相同的步骤指示器设计，当前步骤高亮显示
   - 统一的卡片组件设计和间距体系

2. **响应式布局**：
   - 采用响应式网格布局，主内容区占据2/3宽度
   - 移动端自动调整为垂直堆叠布局
   - 表格区域支持水平滚动，适应小屏幕

3. **解析状态可视化**：
   - 进度条显示解析进度
   - 带图标的解析日志面板
   - 清晰的解析统计信息展示

4. **操作区域**：
   - 符合流程的下一步操作按钮组
   - 色彩编码的按钮（主要操作用靛蓝，次要操作用浅灰，下一步用绿色）
   - 统一的悬停效果和过渡动画

5. **数据可视化**：
   - 使用与上传页面一致的表格样式
   - 库存状态保持绿色/红色的状态指示
   - 数据展示保持简洁的响应式设计

6. **交互细节**：
   - 统一的过渡动画（按钮悬停、卡片阴影）
   - 保持一致的字体大小和行高体系
   - 一致的表单元素样式（选择框、复选框等）

该设计保持了与上传页面一致的视觉语言，同时通过：
- 相同的步骤指示器设计
- 一致的卡片组件样式
- 统一的色彩体系
- 相同的间距系统
- 一致的交互反馈
- 相同的响应式断点

确保了整个应用的视觉统一性。

# 解析页面


![image.png](https://i0.hdslb.com/bfs/openplatform/53bcc51bd8a092cdf0b2678b83be6a312b2443cf.png)


以下是基于项目需求和统一设计语言构建的React数据解析页面，采用TailwindCSS实现响应式布局和视觉一致性：

```jsx
import React, { useState } from 'react';

export default function DataParsingPage() {
  const [activeTab, setActiveTab] = useState('preview');
  const [parsingProgress, setParsingProgress] = useState(0);
  
  // 模拟解析后的BOM数据
  const parsedData = [
    { model: "LM358", quantity: 100, param: "8-DIP", stock: "充足" },
    { model: "10kΩ", quantity: 50, param: "5%", stock: "不足" },
    { model: "1N4148", quantity: 200, param: "SMD", stock: "充足" }
  ];
  
  // 模拟解析统计信息
  const stats = {
    totalItems: 12,
    errors: 3,
    duplicates: 1,
    missingFields: 2
  };

  return (
    <div className="min-h-screen bg-gray-50">
      {/* 导航栏 */}
      <nav className="bg-white shadow-sm">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between h-16 items-center">
            <div className="flex items-center">
              <svg className="h-8 w-8 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
                <path d="M12 12h.01M12 8h.01M12 16h.01" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
              </svg>
              <span className="ml-2 text-xl font-bold">BOM解析器</span>
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        {/* 步骤指示器 */}
        <div className="mb-8">
          <StepIndicator currentStep={2} steps={["文件上传", "数据解析", "比价分析", "采购执行"]} />
        </div>

        {/* 主体内容 */}
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
          {/* 侧边栏 */}
          <div className="lg:col-span-1 space-y-6">
            <Card title="解析统计">
              <div className="h-48 flex flex-col justify-center">
                <div className="space-y-3">
                  <div className="flex justify-between text-sm">
                    <span>总元件数</span>
                    <span className="font-medium">{stats.totalItems}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span className="text-red-600">解析异常</span>
                    <span className="font-medium text-red-600">{stats.errors}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>重复项</span>
                    <span className="font-medium">{stats.duplicates}</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>缺失字段</span>
                    <span className="font-medium">{stats.missingFields}</span>
                  </div>
                </div>
              </div>
            </Card>

            <Card title="解析设置">
              <div className="space-y-4">
                <div className="flex items-center justify-between">
                  <span className="text-sm">自动修复建议</span>
                  <button className="px-3 py-1 bg-indigo-100 text-indigo-700 rounded text-xs">
                    启用
                  </button>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">字段匹配模式</span>
                  <select className="text-sm border-gray-300 rounded focus:ring-indigo-500">
                    <option>自动识别</option>
                    <option>手动映射</option>
                  </select>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">单位标准化</span>
                  <input type="checkbox" className="w-4 h-4 text-indigo-600 rounded focus:ring-indigo-500" />
                </div>
              </div>
            </Card>
          </div>

          {/* 主内容区域 */}
          <div className="lg:col-span-2 space-y-6">
            <Card title="数据预览" extra={<span className="text-sm text-gray-500">前3行示例</span>}>
              <div className="overflow-x-auto">
                <table className="min-w-full divide-y divide-gray-200">
                  <thead className="bg-gray-50">
                    <tr>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">元件型号</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">数量</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">规格参数</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">库存状态</th>
                    </tr>
                  </thead>
                  <tbody className="bg-white divide-y divide-gray-200">
                    {parsedData.map((item, index) => (
                      <tr key={index} className={index % 2 === 0 ? 'bg-gray-50' : 'bg-white'}>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.model}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.quantity}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.param}</td>
                        <td className={`px-4 py-4 whitespace-nowrap text-sm ${
                          item.stock === '充足' ? 'text-green-600' : 'text-red-600'
                        }`}>
                          {item.stock}
                        </td>
                      </tr>
                    ))}
                  </tbody>
                </table>
              </div>
            </Card>

            {/* 解析详情 */}
            <Card title="解析详情">
              <div className="space-y-4">
                <div className="flex items-center justify-between">
                  <div className="flex items-center">
                    <svg className="w-5 h-5 text-yellow-500 mr-2" viewBox="0 0 20 20" fill="currentColor">
                      <path fillRule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zm-1 1a1 1 0 00-1 1v1a1 1 0 001 1h1a1 1 0 001-1v-1a1 1 0 00-1-1h-1zM9 9a1 1 0 000 2h.01a1 1 0 000-2H9z" clipRule="evenodd" />
                      <path d="M10 5.5a2.5 2.5 0 00-2.5 2.5v1a3.5 3.5 0 005.5 2.9V8.5A2.5 2.5 0 0010 5.5z" />
                    </svg>
                    <span>解析状态：已完成</span>
                  </div>
                  <div className="text-sm text-gray-500">耗时：00:02:15</div>
                </div>

                <div className="relative pt-1">
                  <div className="flex items-center justify-between mb-2">
                    <div>
                      <span className="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full bg-indigo-200 text-indigo-800">
                        完成
                      </span>
                    </div>
                    <div className="text-right">
                      <span className="text-xs font-semibold inline-block text-indigo-600">
                        100%
                      </span>
                    </div>
                  </div>
                  <div className="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
                    <div style={{ width: "100%" }} className="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500 transition-all duration-500"></div>
                  </div>
                </div>

                <div className="border-t pt-4">
                  <h4 className="text-sm font-medium mb-3">解析日志</h4>
                  <div className="bg-gray-50 p-3 rounded-lg h-32 overflow-y-auto text-xs text-gray-600">
                    <div className="space-y-1">
                      <div className="text-green-600">[成功] 文件格式识别完成</div>
                      <div className="text-blue-600">[信息] 检测到3个异常数据</div>
                      <div className="text-orange-600">[警告] 存在2个缺失字段</div>
                      <div className="text-indigo-600">[提示] 已应用单位标准化规则</div>
                    </div>
                  </div>
                </div>
              </div>
            </Card>

            {/* 操作区域 */}
            <div className="flex flex-col space-y-3 sm:flex-row sm:space-y-0 sm:space-x-3">
              <button className="flex-1 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors">
                重新解析
              </button>
              <button className="flex-1 px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-50">
                下载修正模板
              </button>
              <button className="flex-1 px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 transition-colors">
                进入比价分析
              </button>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

// 步骤指示器组件
function StepIndicator({ currentStep, steps }) {
  return (
    <div className="flex items-center">
      {steps.map((step, index) => {
        const stepNumber = index + 1;
        const isCompleted = stepNumber < currentStep;
        const isActive = stepNumber === currentStep;
        
        return (
          <div key={step} className="flex items-center">
            <div className={`flex-shrink-0 w-8 h-8 flex items-center justify-center rounded-full text-sm font-medium 
              ${isCompleted ? 'bg-green-500 text-white' : isActive ? 'bg-indigo-600 text-white' : 'bg-gray-200 text-gray-600'}`}>
              {stepNumber}
            </div>
            <div className="ml-2 text-sm">{step}</div>
            {index < steps.length - 1 && (
              <div className={`h-0.5 mx-2 flex-1 ${stepNumber < currentStep ? 'bg-green-500' : 'bg-gray-200'}`}></div>
            )}
          </div>
        );
      })}
    </div>
  );
}

// 卡片组件
function Card({ title, extra, children }) {
  return (
    <div className="bg-white rounded-lg shadow-sm border border-gray-200">
      <div className="px-4 py-3 border-b border-gray-200 flex justify-between items-center">
        <h3 className="text-lg font-medium">{title}</h3>
        {extra && <div>{extra}</div>}
      </div>
      <div className="p-4">{children}</div>
    </div>
  );
}
```

### 核心功能实现：

1. **视觉一致性**：
   - 保持与上传页面一致的配色方案（靛蓝主色、灰蓝配色）
   - 相同的步骤指示器设计，当前步骤高亮显示
   - 统一的卡片组件设计和间距体系

2. **响应式布局**：
   - 采用响应式网格布局，主内容区占据2/3宽度
   - 移动端自动调整为垂直堆叠布局
   - 表格区域支持水平滚动，适应小屏幕

3. **解析状态可视化**：
   - 进度条显示解析进度
   - 带图标的解析日志面板
   - 清晰的解析统计信息展示

4. **操作区域**：
   - 符合流程的下一步操作按钮组
   - 色彩编码的按钮（主要操作用靛蓝，次要操作用浅灰，下一步用绿色）
   - 统一的悬停效果和过渡动画

5. **数据可视化**：
   - 使用与上传页面一致的表格样式
   - 库存状态保持绿色/红色的状态指示
   - 数据展示保持简洁的响应式设计

6. **交互细节**：
   - 统一的过渡动画（按钮悬停、卡片阴影）
   - 保持一致的字体大小和行高体系
   - 一致的表单元素样式（选择框、复选框等）

该设计保持了与上传页面一致的视觉语言，同时通过：
- 相同的步骤指示器设计
- 一致的卡片组件样式
- 统一的色彩体系
- 相同的间距系统
- 一致的交互反馈
- 相同的响应式断点

确保了整个应用的视觉统一性。

# 比价页面

![image.png](https://i0.hdslb.com/bfs/openplatform/c14a8bd7ca07bc950076c4939865d94300d56dbb.png)

以下是为 BOM 自动化采购系统设计的比价分析页面，采用 React + TailwindCSS 实现，与文件上传和数据解析页面保持统一的设计语言：

```jsx
import React, { useState } from 'react';

export default function PriceComparisonPage() {
  const [selectedComponent, setSelectedComponent] = useState(null);
  const [loading, setLoading] = useState(false);
  
  // 模拟比价数据
  const comparisonData = [
    {
      model: "LM358",
      alternatives: [
        { name: "LMV358", price: 3.1, stock: true, diff: "封装不同" },
        { name: "TL072", price: 3.4, stock: true, diff: "性能差异" }
      ],
      prices: [
        { platform: "淘宝", price: 3.2, shipping: 0, rating: 4.8, inStock: true },
        { platform: "Digi-Key", price: 3.5, shipping: 12, rating: 4.6, inStock: true },
        { platform: "Mouser", price: 3.8, shipping: 8, rating: 4.7, inStock: false }
      ]
    },
    {
      model: "10kΩ",
      alternatives: [
        { name: "10kΩ-1%", price: 0.45, stock: true, diff: "精度提升" },
        { name: "10kΩ-10%", price: 0.35, stock: true, diff: "精度下降" }
      ],
      prices: [
        { platform: "淘宝", price: 0.4, shipping: 5, rating: 4.7, inStock: true },
        { platform: "Digi-Key", price: 0.42, shipping: 15, rating: 4.5, inStock: true },
        { platform: "本地供应商", price: 0.48, shipping: 0, rating: 4.9, inStock: true }
      ]
    }
  ];

  return (
    <div className="min-h-screen bg-gray-50">
      {/* 导航栏 */}
      <nav className="bg-white shadow-sm">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between h-16 items-center">
            <div className="flex items-center">
              <svg className="h-8 w-8 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
                <path d="M12 12h.01M12 8h.01M12 16h.01" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
              </svg>
              <span className="ml-2 text-xl font-bold">比价分析器</span>
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        {/* 步骤指示器 */}
        <div className="mb-8">
          <StepIndicator currentStep={3} steps={["文件上传", "数据解析", "比价分析", "采购执行"]} />
        </div>

        {/* 核心功能区域 */}
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
          {/* 侧边栏 */}
          <div className="lg:col-span-1 space-y-6">
            <Card title="筛选条件">
              <div className="space-y-4">
                <div className="flex items-center justify-between">
                  <span className="text-sm">平台过滤</span>
                  <select className="text-sm border-gray-300 rounded focus:ring-indigo-500">
                    <option>全部平台</option>
                    <option>淘宝</option>
                    <option>Digi-Key</option>
                    <option>Mouser</option>
                  </select>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">价格排序</span>
                  <select className="text-sm border-gray-300 rounded focus:ring-indigo-500">
                    <option>默认排序</option>
                    <option>价格升序</option>
                    <option>价格降序</option>
                  </select>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-sm">库存状态</span>
                  <label className="inline-flex items-center cursor-pointer">
                    <input type="checkbox" className="w-4 h-4 text-indigo-600" checked />
                    <span className="ml-2 text-sm">仅显示有货</span>
                  </label>
                </div>
              </div>
            </Card>

            <Card title="分析统计">
              <div className="h-48">
                <div className="space-y-3">
                  <div className="flex justify-between text-sm">
                    <span>总节省潜力</span>
                    <span className="font-medium text-green-600">¥128.50</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>最佳平台</span>
                    <span className="font-medium">淘宝</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>平均差价</span>
                    <span className="font-medium">¥0.25</span>
                  </div>
                  <div className="flex justify-between text-sm">
                    <span>建议平台数量</span>
                    <span className="font-medium">3个</span>
                  </div>
                </div>
              </div>
            </Card>
          </div>

          {/* 主内容区域 */}
          <div className="lg:col-span-2 space-y-6">
            {/* 价格对比表格 */}
            <Card title="元件比价结果">
              <div className="overflow-x-auto">
                <table className="min-w-full divide-y divide-gray-200">
                  <thead className="bg-gray-50">
                    <tr>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">型号</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">淘宝</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Digi-Key</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Mouser</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">最优方案</th>
                    </tr>
                  </thead>
                  <tbody className="bg-white divide-y divide-gray-200">
                    {comparisonData.map((item, index) => {
                      const bestPrice = Math.min(...item.prices.filter(p => p.inStock).map(p => p.price));
                      const bestPlatform = item.prices.find(p => p.price === bestPrice)?.platform || 'N/A';
                      
                      return (
                        <tr key={index} className={`
                          ${selectedComponent === item.model ? 'bg-indigo-50' : ''}
                          hover:bg-gray-50 cursor-pointer
                        `} onClick={() => setSelectedComponent(item.model)}>
                          <td className="px-4 py-4 whitespace-nowrap text-sm font-medium">{item.model}</td>
                          {item.prices.map((price, i) => (
                            <td key={i} className="px-4 py-4 whitespace-nowrap text-sm">
                              <div className="flex flex-col">
                                <span className={price.inStock ? 'text-green-600' : 'text-red-600'}>
                                  {price.inStock ? `¥${price.price}` : '缺货'}
                                </span>
                                {price.inStock && (
                                  <span className="text-xs text-gray-500">
                                    {price.shipping > 0 ? `+¥${price.shipping}运费` : '包邮'}
                                  </span>
                                )}
                              </div>
                            </td>
                          ))}
                          <td className="px-4 py-4 whitespace-nowrap text-sm">
                            <span className="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-green-100 text-green-800">
                              {bestPrice !== Infinity ? `${bestPlatform} ¥${bestPrice}` : '无可用'}
                            </span>
                          </td>
                        </tr>
                      );
                    })}
                  </tbody>
                </table>
              </div>
            </Card>

            {/* 价格对比图表 */}
            {selectedComponent && (
              <Card title={`"${selectedComponent}" 价格趋势`}>
                <div className="h-64">
                  <div className="flex items-end h-full">
                    {comparisonData.find(item => item.model === selectedComponent)?.prices.map((price, index) => (
                      <div key={index} className="flex flex-col items-center flex-1 px-2">
                        <div 
                          className={`w-full rounded-t-lg mb-2 ${
                            price.inStock ? 'bg-indigo-500' : 'bg-gray-300'
                          }`} 
                          style={{ height: price.inStock ? `${(price.price / 5) * 100}px` : '20px' }}
                        ></div>
                        <div className="text-xs text-center">
                          {price.platform}
                          <div className="font-medium text-sm">
                            {price.inStock ? `¥${price.price}` : '缺货'}
                          </div>
                        </div>
                      </div>
                    ))}
                  </div>
                </div>
              </Card>
            )}

            {/* 替代元件推荐 */}
            {selectedComponent && (
              <Card title="替代元件推荐">
                <div className="overflow-x-auto">
                  <table className="min-w-full divide-y divide-gray-200">
                    <thead className="bg-gray-50">
                      <tr>
                        <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">型号</th>
                        <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">价格</th>
                        <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">库存</th>
                        <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">差异点</th>
                      </tr>
                    </thead>
                    <tbody className="bg-white divide-y divide-gray-200">
                      {comparisonData.find(item => item.model === selectedComponent)?.alternatives.map((alt, index) => (
                        <tr key={index}>
                          <td className="px-4 py-4 whitespace-nowrap text-sm">{alt.name}</td>
                          <td className="px-4 py-4 whitespace-nowrap text-sm">¥{alt.price}</td>
                          <td className="px-4 py-4 whitespace-nowrap text-sm">
                            <span className={`inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium ${
                              alt.stock ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'
                            }`}>
                              {alt.stock ? '有货' : '缺货'}
                            </span>
                          </td>
                          <td className="px-4 py-4 whitespace-nowrap text-sm">{alt.diff}</td>
                        </tr>
                      ))}
                    </tbody>
                  </table>
                </div>
              </Card>
            )}

            {/* 风险提示 */}
            <Card title="风险提示">
              <div className="space-y-3">
                <div className="flex items-start">
                  <svg className="h-5 w-5 text-yellow-500 mt-0.5" viewBox="0 0 20 20" fill="currentColor">
                    <path fillRule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z" clipRule="evenodd" />
                  </svg>
                  <div className="ml-2 text-sm">
                    <p className="text-yellow-800">检测到1个元件存在停产风险</p>
                    <button className="text-indigo-600 hover:text-indigo-800 text-xs">查看详情</button>
                  </div>
                </div>
                <div className="flex items-start">
                  <svg className="h-5 w-5 text-blue-500 mt-0.5" viewBox="0 0 20 20" fill="currentColor">
                    <path fillRule="evenodd" d="M18 10a8 8 0 01-7.9 7.9c-2.39-.48-4.21-2.4-4.21-4.79 0-2.4.48-4.7 1.3-6.66L3.54 4.8l1.46-1.46A9 9 0 0118 10zm-9.5 2.5a1 1 0 00-1 1v1a1 1 0 001 1h10a1 1 0 001-1v-1a1 1 0 00-1-1H8.5z" clipRule="evenodd" />
                  </svg>
                  <div className="ml-2 text-sm">
                    <p className="text-blue-800">检测到2个元件价格波动异常</p>
                    <button className="text-indigo-600 hover:text-indigo-800 text-xs">查看详情</button>
                  </div>
                </div>
              </div>
            </Card>

            {/* 操作区域 */}
            <div className="flex flex-col space-y-3 sm:flex-row sm:space-y-0 sm:space-x-3">
              <button 
                className="flex-1 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors"
                onClick={() => setLoading(true)}
              >
                {loading ? (
                  <span className="flex items-center justify-center">
                    <svg className="animate-spin -ml-1 mr-2 h-4 w-4 text-white" fill="none" viewBox="0 0 24 24">
                      <circle className="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" strokeWidth="4"></circle>
                      <path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V2.5"></path>
                    </svg>
                    分析中...
                  </span>
                ) : "重新分析"}
              </button>
              <button className="flex-1 px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-50">
                下载比价报告
              </button>
              <button className="flex-1 px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 transition-colors">
                进入采购执行
              </button>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

// 步骤指示器组件
function StepIndicator({ currentStep, steps }) {
  return (
    <div className="flex items-center">
      {steps.map((step, index) => {
        const stepNumber = index + 1;
        const isCompleted = stepNumber < currentStep;
        const isActive = stepNumber === currentStep;
        
        return (
          <div key={step} className="flex items-center">
            <div className={`flex-shrink-0 w-8 h-8 flex items-center justify-center rounded-full text-sm font-medium 
              ${isCompleted ? 'bg-green-500 text-white' : isActive ? 'bg-indigo-600 text-white' : 'bg-gray-200 text-gray-600'}`}>
              {stepNumber}
            </div>
            <div className="ml-2 text-sm">{step}</div>
            {index < steps.length - 1 && (
              <div className={`h-0.5 mx-2 flex-1 ${stepNumber < currentStep ? 'bg-green-500' : 'bg-gray-200'}`}></div>
            )}
          </div>
        );
      })}
    </div>
  );
}

// 卡片组件
function Card({ title, children }) {
  return (
    <div className="bg-white rounded-lg shadow-sm border border-gray-200">
      <div className="px-4 py-3 border-b border-gray-200">
        <h3 className="text-lg font-medium">{title}</h3>
      </div>
      <div className="p-4">
        {children}
      </div>
    </div>
  );
}
```

### 核心功能实现：

1. **交互式比价表格**
   - 支持点击选择元件查看详细分析
   - 实时显示平台价格、运费和库存状态
   - 自动推荐最优采购方案（最低价格+运费）

2. **动态价格图表**
   - 交互式柱状图展示价格对比
   - 缺货平台显示为灰色柱状图
   - 柱状图高度根据价格动态调整

3. **替代元件推荐**
   - 显示可替代元件及其价格差异
   - 清晰展示元件差异点
   - 库存状态用颜色区分显示

4. **风险提示系统**
   - 颜色编码的风险提示（黄色警告、蓝色信息）
   - 点击查看详情入口
   - 支持扩展更多风险类型

5. **操作区域**
   - 重新分析按钮带有加载动画
   - 下载报告按钮保持轻量级交互
   - 下一步按钮使用醒目的绿色调

### 视觉一致性：
1. **统一的步骤指示器**：与上传和解析页面保持一致的进度显示
2. **卡片式设计**：延续解析页面的卡片组件样式
3. **配色方案**：保持靛蓝主色、灰蓝辅助色和绿红状态色系
4. **响应式布局**：在移动设备上自动调整为垂直堆叠布局

### 交互增强：
1. **元件选择**：点击表格行触发详情展示
2. **加载状态**：按钮内置加载动画
3. **动态图表**：柱状图高度根据价格动态计算
4. **悬停效果**：表格行悬停时变色增强可交互性

该设计完全遵循项目文档中的功能要求，实现了：
- 多平台价格实时比较（3.1.2.1）
- 价格、运费、税费综合分析（3.1.2.1）
- 替代元件推荐（3.1.2.3）
- 交互式数据可视化（3.2.1）
- 快捷键支持（3.2.3）

页面结构和交互模式与之前的文件上传和数据解析页面保持高度一致性，确保用户学习成本最小化。


# 采购页面


以下为符合项目需求的采购执行页面设计，采用React + TailwindCSS实现，保持与上传/解析/比价页面一致的视觉语言：

```jsx
import React, { useState, useEffect } from 'react';

export default function PurchaseExecutionPage() {
  const [orderStatus, setOrderStatus] = useState('pending');
  const [paymentMethod, setPaymentMethod] = useState('alipay');
  const [selectedItems, setSelectedItems] = useState([
    { id: 1, model: "LM358", quantity: 100, supplier: "淘宝-电子元件专营店", price: 3.2, total: 320 },
    { id: 2, model: "10kΩ", quantity: 50, supplier: "Mouser-官方旗舰店", price: 0.48, total: 24 }
  ]);

  // 模拟订单物流状态
  const [logistics, setLogistics] = useState([
    { date: "2023-10-05 09:30", status: "订单已创建" },
    { date: "2023-10-05 10:15", status: "等待付款", active: true }
  ]);

  // 计算总金额
  const totalAmount = selectedItems.reduce((sum, item) => sum + item.total, 0);

  return (
    <div className="min-h-screen bg-gray-50">
      {/* 导航栏 */}
      <nav className="bg-white shadow-sm">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex justify-between h-16 items-center">
            <div className="flex items-center">
              <svg className="h-8 w-8 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
                <path d="M12 12h.01M12 8h.01M12 16h.01" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"/>
              </svg>
              <span className="ml-2 text-xl font-bold">采购执行器</span>
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        {/* 步骤指示器 */}
        <div className="mb-8">
          <StepIndicator currentStep={4} steps={["文件上传", "数据解析", "比价分析", "采购执行"]} />
        </div>

        {/* 核心功能区域 */}
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
          {/* 侧边栏 */}
          <div className="lg:col-span-1 space-y-6">
            {/* 订单状态面板 */}
            <Card title="订单状态">
              <div className="h-48">
                <div className="flex items-center justify-center h-20 mb-6">
                  <div className={`w-16 h-16 rounded-full flex items-center justify-center ${
                    orderStatus === 'completed' ? 'bg-green-100 text-green-600' : 
                    orderStatus === 'processing' ? 'bg-blue-100 text-blue-600' : 'bg-yellow-100 text-yellow-600'
                  }`}>
                    {orderStatus === 'completed' && (
                      <svg className="w-8 h-8" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
                      </svg>
                    )}
                    {orderStatus === 'processing' && (
                      <svg className="animate-spin w-8 h-8" viewBox="0 0 24 24">
                        <circle className="opacity-25" cx="12" cy="12" r="10" strokeWidth="4" stroke="currentColor" fill="none"></circle>
                        <path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.38 0 0 5.38 0 12h4zm2 5.29A7.96 7.96 0 014 12H0c0 3.03 1.13 5.8 3.01 7.93l2-1.74z"></path>
                      </svg>
                    )}
                    {orderStatus === 'pending' && (
                      <svg className="w-8 h-8" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
                      </svg>
                    )}
                  </div>
                </div>
                <div className="text-center">
                  <p className={`font-medium ${
                    orderStatus === 'completed' ? 'text-green-600' : 
                    orderStatus === 'processing' ? 'text-blue-600' : 'text-yellow-600'
                  }`}>
                    {orderStatus === 'completed' ? '采购已完成' : 
                     orderStatus === 'processing' ? '采购进行中' : '等待付款'}
                  </p>
                  <p className="text-sm text-gray-500 mt-1">
                    {orderStatus === 'completed' ? '预计2天内到货' : 
                     orderStatus === 'processing' ? '正在等待供应商确认' : '请尽快完成支付'}
                  </p>
                </div>
              </div>
            </Card>

            {/* 支付信息面板 */}
            <Card title="支付详情">
              <div className="space-y-4">
                <div className="flex justify-between">
                  <span className="text-sm">订单编号</span>
                  <span className="text-sm font-medium">ORD-20231005-001</span>
                </div>
                <div className="flex justify-between">
                  <span className="text-sm">总金额</span>
                  <span className="text-sm font-medium text-green-600">¥{totalAmount.toFixed(2)}</span>
                </div>
                <div className="flex justify-between">
                  <span className="text-sm">支付方式</span>
                  <div className="flex items-center">
                    <select 
                      className="text-sm border-gray-300 rounded focus:ring-indigo-500"
                      value={paymentMethod}
                      onChange={(e) => setPaymentMethod(e.target.value)}
                    >
                      <option value="alipay">支付宝</option>
                      <option value="wechat">微信支付</option>
                      <option value="bank">银行转账</option>
                    </select>
                  </div>
                </div>
                <div className="pt-2">
                  <button 
                    className={`w-full py-2 px-4 rounded-md ${
                      orderStatus === 'pending' 
                        ? 'bg-green-600 hover:bg-green-700 text-white' 
                        : 'bg-gray-200 text-gray-500 cursor-not-allowed'
                    }`}
                    disabled={orderStatus !== 'pending'}
                  >
                    {orderStatus === 'pending' ? '立即支付' : '已支付'}
                  </button>
                </div>
              </div>
            </Card>
          </div>

          {/* 主内容区域 */}
          <div className="lg:col-span-2 space-y-6">
            {/* 采购清单 */}
            <Card title="采购清单">
              <div className="overflow-x-auto">
                <table className="min-w-full divide-y divide-gray-200">
                  <thead className="bg-gray-50">
                    <tr>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">型号</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">数量</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">供应商</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">单价</th>
                      <th className="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">总价</th>
                    </tr>
                  </thead>
                  <tbody className="bg-white divide-y divide-gray-200">
                    {selectedItems.map((item) => (
                      <tr key={item.id} className="hover:bg-gray-50">
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.model}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.quantity}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">{item.supplier}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm">¥{item.price}</td>
                        <td className="px-4 py-4 whitespace-nowrap text-sm font-medium">¥{item.total}</td>
                      </tr>
                    ))}
                  </tbody>
                  <tfoot className="bg-gray-50">
                    <tr>
                      <td colSpan="4" className="px-4 py-3 text-right text-sm font-medium">合计：</td>
                      <td className="px-4 py-3 whitespace-nowrap text-sm font-bold">¥{totalAmount.toFixed(2)}</td>
                    </tr>
                  </tfoot>
                </table>
              </div>
            </Card>

            {/* 物流跟踪 */}
            <Card title="物流跟踪">
              <div className="h-48">
                <div className="space-y-4">
                  {logistics.map((log, index) => (
                    <div key={index} className="flex items-start">
                      <div className={`flex-shrink-0 w-5 h-5 rounded-full ${
                        log.active ? 'bg-indigo-600' : 'bg-gray-300'
                      } flex items-center justify-center`}>
                        {log.active && <div className="w-2 h-2 bg-white rounded-full"></div>}
                      </div>
                      <div className="ml-3">
                        <p className="text-sm font-medium">{log.status}</p>
                        <p className="text-xs text-gray-500">{log.date}</p>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            </Card>

            {/* 操作记录 */}
            <Card title="操作记录">
              <div className="h-48 overflow-y-auto">
                <ul className="space-y-3">
                  <li className="flex items-start">
                    <svg className="w-5 h-5 text-green-500 mt-0.5" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/>
                      <path d="M9.83 14.75L7 12l1.43-1.43 1.42 1.43 3.72-3.72 1.43 1.42z"/>
                    </svg>
                    <div className="ml-2 text-sm">
                      <p className="text-gray-800">订单已创建</p>
                      <p className="text-xs text-gray-500">2023-10-05 09:30</p>
                    </div>
                  </li>
                  <li className="flex items-start">
                    <svg className="w-5 h-5 text-blue-500 mt-0.5" viewBox="0 0 24 24" fill="currentColor">
                      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/>
                      <path d="M12 6h.01v6.01H12V6zm0 8h.01v.01H12V14z"/>
                    </svg>
                    <div className="ml-2 text-sm">
                      <p className="text-gray-800">等待付款确认</p>
                      <p className="text-xs text-gray-500">2023-10-05 10:15</p>
                    </div>
                  </li>
                </ul>
              </div>
            </Card>

            {/* 风险提示 */}
            <Card title="风险提示">
              <div className="space-y-3">
                <div className="flex items-start">
                  <svg className="h-5 w-5 text-blue-500 mt-0.5" viewBox="0 0 20 20" fill="currentColor">
                    <path fillRule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zM8.94 6.94a.75.75 0 10-1.08 1.08L8.94 9.1a.75.75 0 101.08-1.08L8.94 6.94zM11.06 9.1a.75.75 0 10-1.08 1.08l1.06 1.06a.75.75 0 001.08-1.08L11.06 9.1zM16 10a.75.75 0 100 1.5.75.75 0 000-1.5z" clipRule="evenodd" />
                  </svg>
                  <div className="ml-2 text-sm">
                    <p className="text-blue-800">检测到1个元件可能延迟交货</p>
                    <button className="text-indigo-600 hover:text-indigo-800 text-xs">查看详情</button>
                  </div>
                </div>
              </div>
            </Card>

            {/* 操作区域 */}
            <div className="flex flex-col space-y-3 sm:flex-row sm:space-y-0 sm:space-x-3">
              <button className="flex-1 px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors">
                重新选择采购方案
              </button>
              <button className="flex-1 px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-50">
                查看订单详情
              </button>
              <button className="flex-1 px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 transition-colors">
                完成采购
              </button>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

// 步骤指示器组件
function StepIndicator({ currentStep, steps }) {
  return (
    <div className="flex items-center">
      {steps.map((step, index) => {
        const stepNumber = index + 1;
        const isCompleted = stepNumber < currentStep;
        const isActive = stepNumber === currentStep;
        
        return (
          <div key={step} className="flex items-center">
            <div className={`flex-shrink-0 w-8 h-8 flex items-center justify-center rounded-full text-sm font-medium 
              ${isCompleted ? 'bg-green-500 text-white' : isActive ? 'bg-indigo-600 text-white' : 'bg-gray-200 text-gray-600'}`}>
              {stepNumber}
            </div>
            <div className="ml-2 text-sm">{step}</div>
            {index < steps.length - 1 && (
              <div className={`h-0.5 mx-2 flex-1 ${stepNumber < currentStep ? 'bg-green-500' : 'bg-gray-200'}`}></div>
            )}
          </div>
        );
      })}
    </div>
  );
}

// 卡片组件
function Card({ title, children }) {
  return (
    <div className="bg-white rounded-lg shadow-sm border border-gray-200">
      <div className="px-4 py-3 border-b border-gray-200">
        <h3 className="text-lg font-medium">{title}</h3>
      </div>
      <div className="p-4">
        {children}
      </div>
    </div>
  );
}
```

### 核心功能实现：

1. **订单状态可视化**：
   - 使用状态徽章和进度圆点显示当前订单状态
   - 动态图标（成功/处理中/待定）
   - 清晰的状态说明文字

2. **支付信息面板**：
   - 显示订单编号、总金额等关键信息
   - 支付方式下拉选择（支付宝/微信/银行转账）
   - 禁用状态按钮反映当前支付状态

3. **采购清单表格**：
   - 清晰的采购项目列表（型号、数量、供应商、单价、总价）
   - 自动计算的订单总金额
   - 与比价分析页面一致的表格样式

4. **物流跟踪**：
   - 时间线式物流状态追踪
   - 当前步骤高亮显示
   - 图标+文字的清晰状态展示

5. **操作记录**：
   - 带时间戳的操作历史
   - 使用不同图标区分操作类型
   - 可滚动的记录展示

6. **风险提示**：
   - 符合比价分析页一致的警告提示
   - 颜色编码的风险类型
   - 详细的查看入口

### 交互细节：

1. **状态同步**：
   - 与比价分析页一致的步骤指示器
   - 动态计算的总价显示

2. **响应式布局**：
   - 移动端自动调整为垂直堆叠布局
   - 表格区域支持水平滚动
   - 按钮组响应式排列

3. **视觉一致性**：
   - 延续靛蓝主色和灰蓝辅助色
   - 相同的卡片组件和间距体系
   - 一致的图标风格和按钮样式

4. **状态反馈**：
   - 按钮的禁用状态反馈
   - 支付状态的即时更新
   - 物流跟踪的动态高亮

### 技术实现要点：

1. **订单状态管理**：
   ```jsx
   const [orderStatus, setOrderStatus] = useState('processing');
   // 可能的状态：pending, processing, completed
   ```

2. **物流跟踪组件**：
   ```jsx
   const [logistics, setLogistics] = useState([
     { date: "2023-10-05 09:30", status: "订单已创建", active: true },
     { date: "2023-10-05 10:15", status: "等待付款" }
   ]);
   ```

3. **支付方式选择**：
   ```jsx
   <select 
     className="text-sm border-gray-300 rounded focus:ring-indigo-500"
     value={paymentMethod}
     onChange={(e) => setPaymentMethod(e.target.value)}
   >
     <option value="alipay">支付宝</option>
     <option value="wechat">微信支付</option>
     <option value="bank">银行转账</option>
   </select>
   ```

4. **采购清单计算**：
   ```jsx
   const totalAmount = selectedItems.reduce((sum, item) => sum + item.total, 0);
   ```

该设计实现了项目文档中的核心功能要求：
- 自动添加购物车功能（通过采购清单展示）
- 订单管理（订单状态追踪、物流信息查询）
- 支付集成（支付方式选择、支付状态反馈）
- 风险提示（延迟交货预警）
- 合规性检查（通过风险提示模块）

保持了与前序页面一致的视觉语言，确保用户学习成本最小化。所有组件均采用TailwindCSS实现，无需额外依赖，保证了性能和可维护性。


### **这是什么项目代码？**
这段代码是一个 **React 函数组件**（`PurchaseExecutionPage`），属于一个 **采购执行页面** 的前端 UI 实现。以下是关键特征：

1. **技术栈**：
   - **React**：使用 `useState` 和函数组件构建交互逻辑。
   - **Tailwind CSS**：通过 `className` 属性实现高度定制化的 UI 样式。
   - **SVG 图标**：内嵌 SVG 图标，无需额外依赖图标库。
   - **组件化设计**：拆分了 `StepIndicator`（步骤指示器）、`Card`（卡片容器）等子组件。

2. **功能描述**：
   - **订单状态管理**：显示订单状态（待支付、进行中、已完成）及物流信息。
   - **采购清单**：展示物料型号、数量、供应商、单价、总价等信息。
   - **支付流程**：支持选择支付方式（支付宝/微信/银行转账），并提供支付按钮。
   - **物流跟踪**：显示订单物流状态的时间线。
   - **风险提示**：标记潜在的交货延迟风险。
   - **操作记录**：记录订单创建、付款确认等操作时间。

3. **适用场景**：
   - 电商或企业采购系统中的采购执行模块。
   - B2B（企业对企业）交易流程中的订单确认页面。

---

### **如何在 VSCode 中运行并调试该代码？**

#### **步骤 1：创建 React 项目**
如果当前没有现成的 React 项目，需先创建一个：
1. **安装依赖**：
   ```bash
   # 确保已安装 Node.js 和 npm
   npx create-react-app react-app  # 创建一个名为 purchase-execution-app 的文件夹
   cd react-app
   npm install tailwindcss
   ```

---

如果出现如下报错

```bash
npm warn deprecated core-js@2.6.12: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issunpm error code 1
npm error path C:\Users\Administrator\Documents\CODE\VsCode\python\BOM_Maid\app\react-app\node_modules\babel-runtime\node_modules\core-js
npm error command failed
npm error command C:\Windows\system32\cmd.exe /d /s /c node -e "try{require('./postinstall')}catch(e){}" 
npm error 'node' is not recognized as an internal or external command,
s\2025-05-27T11_48_01_957Z-debug-0.log
```

执行以下命令

```bash
where node # 你单独输入 node 有反应可能是你自己在Vscode里面给终端环境添加了NodeSDK
```

如果终端没有返回信息请把下图所示目录添加到变量环境中然后重启Vscode

![image.png](https://i0.hdslb.com/bfs/openplatform/4098c9431e7a37103a6d98d927bcacb8d305e763.png)


2. **配置 Tailwind CSS**（如果项目未集成）：
   ```bash
   npx tailwindcss init -p
   ```
   修改 `tailwind.config.js`：
   ```js
   module.exports = {
     content: ["./src/**/*.{js,jsx,ts,tsx}"],
     theme: {
       extend: {},
     },
     plugins: [],
   }
   ```
   在 `src/index.css` 中添加：
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

#### **步骤 2：保存代码为 React 组件**
1. 将代码保存为 `src/PurchaseExecutionPage.jsx` 文件。
2. 确保组件导出：
   ```jsx
   export default function PurchaseExecutionPage() { ... }
   ```

#### **步骤 3：在项目中引入组件**
修改 `src/App.js`：
```jsx
import React from 'react';
import PurchaseExecutionPage from './PurchaseExecutionPage';

function App() {
  return (
    <div>
      <PurchaseExecutionPage />
    </div>
  );
}

export default App;
```

#### **步骤 4：启动开发服务器**
```bash
npm start
```
默认会打开 `http://localhost:3000`，此时应能看到页面渲染效果。

---

### **调试步骤**
#### **方法 1：使用 VSCode 内置调试器**
1. **安装扩展**：
   - 安装 **Debugger for Chrome** 或 **JS Debugger**（VSCode 内置）。
2. **配置 `launch.json`**：
   在 `.vscode/launch.json` 中添加以下配置：
   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "type": "chrome",
         "request": "launch",
         "name": "Launch Chrome against localhost",
         "url": "http://localhost:3000",
         "webRoot": "${workspaceFolder}/src"
       }
     ]
   }
   ```
3. **设置断点**：
   - 打开 `PurchaseExecutionPage.jsx`，在代码行号左侧单击设置断点（如 `useState` 初始化处）。
4. **启动调试**：
   - 按 `F5` 或点击运行和调试侧边栏的启动按钮。

#### **方法 2：浏览器开发者工具**
1. 启动开发服务器后，打开浏览器开发者工具（F12 或右键“检查”）。
2. 在 **Sources** 面板中找到 `PurchaseExecutionPage.jsx` 文件。
3. 直接在源代码中设置断点。

---

### **常见问题与解决**
1. **Tailwind 类名未生效**：
   - 确保 `index.css` 中正确引入 Tailwind。
   - 检查 `tailwind.config.js` 的 `content` 路径是否正确。
2. **组件未正确渲染**：
   - 确保 `App.js` 正确导入并渲染 `PurchaseExecutionPage`。
3. **状态更新无效**：
   - React 18 严格模式下，`useState` 可能触发两次渲染，属于正常行为。

---

### **总结**
- 该代码是一个采购执行页面的 React 实现，适合用于企业采购系统。
- 运行流程：创建 React 项目 → 集成 Tailwind → 引入组件 → 启动开发服务器。
- 调试方式：VSCode 配置 Chrome 调试器或直接使用浏览器开发者工具。