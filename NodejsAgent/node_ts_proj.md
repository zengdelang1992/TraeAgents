# 如何创建一个默认的typescrpit项目
注意:
先需要确认使用哪个包管理工具，比如优先使用pnmp，下面的步骤使用npm命令，但是如果有推荐的包管理工具需要替换对应的包管理工具来执行，没有的情况下才用下面步骤推荐的命令

1 先询问用户希望在哪里创建typescrpit项目,不要擅自自动执行，这一步需要用户确认
  可以给用户2个选择，在当前项目的根目录下创建，或者用户给出一个指定路径，在对应路径下创建项目，只有获取到创建路径后才能执行后续步骤
2 确定路径后，初始化项目
  执行npm init -y生成package.json
  创建2个文件夹dist和src,修改package.json中两项配置为"outDir": "./dist", "rootDir": "./src"
3 安装typescript和ts-node
  npm install --save-dev typescript
  npm install --save-dev ts-node
4 在src中添加示例代码
  创建一个示例代码src/index.ts,内容如下：
  console.log('Hello, TypeScript!');
5 创建项目说明文档（README.md）
  加入技术栈说明
6 创建.gitignore忽略常见的文件和文件夹
  创建一个.gitignore文件，可参考忽略的内容如下：
  node_modules/
  dist/
  *.log
  *.tmp
  .DS_Store
  .vscode/
  .idea/
  .env
  .env.local
  .env.test
  .env.production
  .env.development
  .env.staging
  .env.preview
  .env.qa
  .env.prod
  .env.production
  .env.prod
  .env.production
7 生成vscode需要的/.vscode/launch.json
  参考ts-node的文档, 内容如下：
    {
        "version": "0.2.0",
        "configurations": [
            {
                "type": "node",
                "request": "launch",
                "name": "Debug with ts-node",
                "args": ["${relativeFile}"],
                "runtimeArgs": ["-r", "ts-node/register"],
                "cwd": "${workspaceRoot}",
                "protocol": "inspector",
                "internalConsoleOptions": "openOnSessionStart",
                "skipFiles": ["<node_internals>/**", "node_modules/**"]
            }
        ]
    }
8 验证了项目可以正常编译和运行