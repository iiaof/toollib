<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ScopedSlotDemo</title>
</head>
<body>
    <div id="app">
        <slot-component :url="website.url">
            <template v-slot="slotProps">
                {{slotProps.data.title}}
            </template>
        </slot-component>
    </div>
    <template id="cpn">
          <a :href="url">
            <solt :data="website">
              {{website.title}}
            </solt>
          </a>
    </template>
</body>
<script src="./vue.min.js"></script>
<script>
    // 父组件通过插槽使用子组件的data
    const SlotComponent = {
        template: '#cpn',
        props: {
            url: {
                type: String,
                default: ''
            }
        },
        data() {
            return {
                website: {
                    url: 'http://child.com/',
                    title: 'child_title'
                }
            }
        }
    };

    new Vue({
        el: '#app',
        data: {
            name: 'parent',
            website: {
                url: 'http://parent.com',
                title: 'parent_title'
            }
        },
        components: {
            SlotComponent
        }
    })

</script>
</html>
