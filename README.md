# simple-marko-router

## Routing for markojs

- Provides two marko tags: <router ... /> and &lt;aa href="" />
- Also availabe in short form: router and aa

### npm install

<code>
  npm install https://github.com/scriptmaster/simple-marko-router
</code>

### yarn add

<code>
  yarn add https://github.com/scriptmaster/simple-marko-router
</code>

## First step: Set up the router in an app component

<code>
  router ...
</code>

## Second and further steps: Link to a router page

<code>
  aa href="/"
</code>

## Uses pushstate

Uses HTML5 pushstate.

# Simple sample

<code>
	class {

		onCreate(input) {
			const routes = this.getRoutes();
		}

		async onMount() {
		}

		onRouterUpdated() {
			const router = this.getComponent('router');
			const routeData = router.state.routeData;
			this.update();
		}

		onRouteComponentMount() {
			console.log('onRouteComponentMount', this.getComponent('router').state.routeData)
		}

		getRoutes() {
			return [
				{ path: '/', component: require('src/pages/landing') },
				{ path: '/manage', component: require('src/pages/manage/list-collections') },
				{ path: '/manage/:collection', component: require('src/pages/manage/collection') },
			]
		}

	}

	.content
		router routes=state.routes on-update('onRouterUpdated') key='router' on-routeComponentMount('onRouteComponentMount')
</code>
