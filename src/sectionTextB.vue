<template>
    <div class="text_B">
        <!-- wwManager:start -->
        <wwSectionEditMenu v-bind:sectionCtrl="sectionCtrl"></wwSectionEditMenu>
        <!-- wwManager:end -->

        <wwObject class="background" v-bind:ww-object="section.data.background" ww-category="background"></wwObject>

        <div class="container">
            <div class="section-padding">
                <div class="row">
                    <div class="title-container">
                        <h1 class="title">
                            <wwObject v-bind:ww-object="section.data.title"></wwObject>
                        </h1>
                    </div>

                    <div class="subtitle-container">
                        <wwObject class="subtitle" v-bind:ww-object="section.data.subtitle1"></wwObject>
                        <wwObject class="subtitle" v-bind:ww-object="section.data.subtitle2"></wwObject>
                        <wwObject class="subtitle" v-bind:ww-object="section.data.subtitle3"></wwObject>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: "text_B",
    props: {
        sectionCtrl: Object
    },
    data() {
        return {}
    },
    computed: {
        section() {
            return this.sectionCtrl.get();
        }
    },
    created() {
        this.section.data = this.section.data || {}

        if (!this.section.data.background) {
            this.section.data.background = wwLib.wwObject.getDefault({ 
                type: 'ww-image',
                data: {
                    url: 'http://cdn.wewebapp.io/public/images/weweb-wp.png'
                }
            });
        }
        if (!this.section.data.title) {
            this.section.data.title = wwLib.wwObject.getDefault({ type: 'ww-text', data: { color: 'white' } });
        }
        if (!this.section.data.subtitle1) {
            this.section.data.subtitle1 = wwLib.wwObject.getDefault({ type: 'ww-text', data: { color: 'white' } });
        }
        if (!this.section.data.subtitle2) {
            this.section.data.subtitle2 = wwLib.wwObject.getDefault({ type: 'ww-text', data: { color: 'white' } });
        }
        if (!this.section.data.subtitle3) {
            this.section.data.subtitle3 = wwLib.wwObject.getDefault({ type: 'ww-text', data: { color: 'white' } });
        }
        this.sectionCtrl.update(this.section);
    },
    methods: {}
};
</script>

<style scoped>
.text_B {
    width: 100%;
    position: relative;
}

.text_B .background {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
}

.text_B .title {
    margin-top: 10px;
}

.text_B .subtitle {
    margin-top: 10px;
}

.text_B .section-padding {
    padding: 30px 15px
}

.text_B .row {
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    margin-right: -15px;
    margin-left: -15px;
}

.text_B .title-container {
    position: relative;
    width: 100%;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    -ms-flex: 0 0 100%;
    flex: 0 0 100%;
    max-width: 100%;
}

.text_B .subtitle-container {
    position: relative;
    width: 100%;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    -ms-flex: 0 0 100%;
    flex: 0 0 100%;
    max-width: 100%;
}

@media (min-width: 480px) {
    .text_B .title-container {
        -ms-flex: 0 0 33.333333%;
        flex: 0 0 33.333333%;
        max-width: 33.333333%;
    }
    .text_B .subtitle-container {
        -ms-flex: 0 0 66.666666%;
        flex: 0 0 66.666666%;
        max-width: 66.666666%;
    }
}

@media (min-width: 768px) {
    .text_B .section-padding {
        padding: 50px 30px
    }
}

@media (min-width: 992px) {
    .text_B .section-padding {
        padding: 75px 50px
    }
}

@media (min-width: 1200px) {}
</style>
