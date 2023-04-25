<template>
  <div>

        <div id="overlay" @click.self="modalClose">
            <div id="content" class="top_works_content js_works_content">
                <div class="top_works_img-wrapper">
                    <img :src="url" alt="" class="top_works_img">
                </div>
                <div class="top_works_text">
                    <h3 class="top_works_title">{{name}}</h3>
                    <table class="top_works_table">
                        <tr class="top_works_table-tr">
                            <th class="top_works_table-th">制作概要 </th>
                            <td class="top_works_table-td">{{overview}}</td>
                        </tr>
                        <tr class="top_works_table-tr">
                            <th class="top_works_table-th">制作期間 </th>
                            <td class="top_works_table-td">{{period}}</td>
                        </tr>
                        <tr class="top_works_table-tr">
                            <th class="top_works_table-th">工夫点 </th>
                            <td class="top_works_table-td">{{ingenuity}}</td>
                        </tr>
                        <tr class="top_works_table-tr">
                            <th class="top_works_table-th">技術 </th>
                            <td class="top_works_table-td">{{skill}}</td>
                        </tr>
                    </table>
                </div>
                <button class="close_btn" @click.self="modalClose">閉じる</button>
            </div>
            
        </div>
  </div>
</template>

<script>
export default {
    props:['url', 'name', 'overview', 'period', 'ingenuity', 'skill'],
    methods: {
        modalClose() {
            this.$emit('is-close', false)
        }
    }
}

</script>

<style>
    #overlay{
        z-index:50;
        position:fixed;
        top:0;
        left:0;
        width:100%;
        height:100%;
        background-color:rgba(0,0,0,0.5);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #content{
        z-index:100;
        background:#fff;
        width: 90%;
        max-width: 500px;
    }

    .close_btn {
        display: block;
    }
</style>