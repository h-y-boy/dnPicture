<template>
    <view>
        <view class="home_tab">
            <view class="home_tab_title">
                <view class="title_inner">
                    <uni-segmented-control :current="current" :values="items.map(v => v.title)" @clickItem="onClickItem"
                        styleType="text" activeColor="#d4237a"></uni-segmented-control>
                </view>
                <view class="iconfont iconsearch"></view>
            </view>
            <view class="home_tab_content">
                <view v-if="current === 0">
                    <HomeRecommand></HomeRecommand>
                </view>
                <view v-if="current === 1">
                    <HomeCategory></HomeCategory>
                </view>
                <view v-if="current === 2">
                    <HomeNew></HomeNew>
                </view>
                <view v-if="current === 3">
                    <HomeAlbum></HomeAlbum>
                </view>
            </view>
        </view>
    </view>
</template>

<script>
import { uniSegmentedControl } from '@dcloudio/uni-ui'
import HomeAlbum from './home-album/index.vue'
import HomeCategory from './home-category/index.vue'
import HomeNew from './home-new/index.vue'
import HomeRecommand from './home-recommand/index.vue'
export default {
    components: {
        HomeAlbum,
        HomeCategory,
        HomeNew,
        HomeRecommand,
        uniSegmentedControl
    },
    data() {
        return {
            items: [
                { title: "推荐" },
                { title: "分类" },
                { title: "最新" },
                { title: "专辑" },
            ],
            current: 0
        };
    },

    methods: {
        onClickItem(e) {
            if (this.current != e.currentIndex) {
                this.current = e.currentIndex;
            }
        }
    }
}
</script>

<style lang="scss">
.home_tab {
    .home_tab_title {
        position: relative;

        .title_inner {
            width: 60%;
            margin: 0 auto;
        }

        .iconsearch {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            right: 5%;
        }
    }
}
</style>
