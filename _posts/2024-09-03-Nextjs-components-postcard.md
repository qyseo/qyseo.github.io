## Nextjs核心概念

组件Components之PostCard

### 1、创建 PostCard 组件

申明一个组件,需要在`components`目录下创建相应的`tsx`文件,比如`postCard`组件

```tsx
import React from 'react';
//需要用到image、moment时间转换、和Link属性
import Image,moment,Link from 'next/image','moment','next/link';

const PostCard = ( {post} ) => (
	//card的DIV样式
);
//导出给需要的布局使用该组件
export default PostCard;

```

### 2、使用 PostCard 组件

组件创建完成,需要被页面使用,假设我们在首页使用：pages\index.js

```js
// pages\index.js v1
import {PostCard} from "../components";

export default function Home( {posts} ){
  return (
  	<div>
    	<PostCard />
    </div>
  );
}
```

考虑到这是一个被循环的组件,所以我们应该使用`map`

```js
// pages\index.js v2
import {PostCard} from "../components";

export default function Home( {posts} ){
  return (
  	<div>
    	<ul>
    		<li>
    			{posts.map((post,index) => (
  					<PostCard key={index} post={post.node} />
  				))}
    		</li>
    	</ul>
    </div>
  );
}
```

把当前文章的索引和节点传入,以方便graphql找到相应的信息,posts是由graphqlAPI获取的所有文章json,下面演示了如何传入

```js
// pages\index.js
import {getPosts} from '../services';

export async function getStaticProps(){
  const posts = (await getPosts()) || [];
  
  return { props: {posts} };
  
}
```

### 3、请求 PostCard 数据

props在react中的意思,就是指在组件之间传递的数据.从这里我们得到了posts数据.现在我们回service\index.js文件中看看`posts`数据是怎么来的.

```js
// services\index.js
import {request,gql} from 'graphql-request';
//定义api地址,这里使用的是graphql cms,这个常量url被写在app目录下的.env文件中
const graphqlAPI = process.env.NEXT_PUBLIC_GRAPHCMS_ENDPOINT;

export const getPosts = async() => {
  //执行相应的数据请求消息,指定获取哪些字段
  const query = gql`....`;
  
  const result = await request(graphqlAPI, query); //执行
  
  return result.postsConnection.edges; //这是graphql的json节点路径
};
```

至此,一个完整的postCard创建,请求数据和使用数据,呈现完成！





