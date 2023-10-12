<template>
  <div>
    <div class="wrapper">
      <table>
        <thead>
          <th>Title</th>
          <th>Tags</th>
          <th>Column 1</th>
          <th>Column 2</th>
          <th>Column 3</th>
        </thead>
        <tbody>
          <td>
            Testing 123
          </td>
          <td>
            <div style="min-width: 556px;">
              <div class="tag-list">
                <template v-for="(tag, index) in tagList" :key="index">
                  <template v-if="tag.type">
                    <span class="plus-wrapper">
                      <div class="plus">
                        +{{ tag.name }}
                      </div>
                    </span>
                    <span style="flex-basis: 100%; height: 0;"></span>
                  </template>
                  <span v-else class="tag">
                    {{ tag.name }}
                  </span>
                </template>
              </div>
            </div>
          </td>
          <td>
            content 3
          </td>
          <td>
            content 4
          </td>
          <td>
            content 4
          </td>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tagList: [
        { name: 'Tag 1  Tag 1Tag 1Tag 1Tag 1Tag 1' },
        { name: 'Tag 2' },
        { name: 'Tag 3' },
        { name: 'Tag 4' },
        { name: 'Tag 5' },
        { name: 'Tag 6' },
        { name: 'Tag 7' },
        { name: 'Tag 8' },
        { name: 'Tag 9' },
        { name: 'Tag 10' },
        { name: 'Tag 11' },
        { name: 'Tag 12' },
        { name: 'Tag 13' },
        { name: 'Tag 14' },
        { name: 'Tag 15' },
        { name: 'Tag 16' },
        { name: 'Tag 17' },
        { name: 'Tag 18' },
        { name: 'Tag 19' },
      ]
    }
  },
  mounted() {
    const tagList = document.querySelector('.tag-list');
    this.insertAddMoreButton(tagList.children);
  },
  methods: {
    insertAddMoreButton() {
      const tagList = document.querySelector('.tag-list').children;
      let i = 0;
      let wrapLocation = null;
      let hiddenItems = [];

      for(let item of tagList) {
        if(item.offsetTop > 45) {
          if(!wrapLocation) {
            wrapLocation = i -1;
          }
          hiddenItems.push(item);
        }
        i++;
      }

      if(wrapLocation) this.tagList.splice(wrapLocation, 0, { name: hiddenItems.length + 1, type: 'plus' });
    }
  }
}
</script>

<style scoped>
.wrapper {
  /* max-width: 1152px; */
  width: 100%;
  margin: 0 auto;
  padding: 4rem 0;
}
table {
  width: 100%;
  border: 1px solid #ccc;
  border-spacing: 0;
  border-collapse: collapse;
}
table th {
  text-align: left;
  font-weight: 700;
  padding: 0.5rem 1rem;
  background: #ccc;
  border: 1px solid #ccc;
}
table td {
  padding: 0.5rem 1rem;
  border: 1px solid #ccc;
}
.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
  height: 62px;
  overflow: hidden;
}
.tag-list .tag {
  display: block;
  border: 1px solid #000;
  font-size: 0.75rem;
  padding: 0.25rem 1rem;
  border-radius: 0.5rem;
  background: #000;
  color: #fff;
  text-align: left;
  max-width: 180px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
.tag-list .plus-wrapper {
  display: block;
  padding: 0;
  background: none;
  border: none;
}
.tag-list .plus {
  font-size: 0.75rem;
  padding: 0.25rem 1rem;
  background: #fff;
  border: 1px solid #ccc;
  color: #000;
  border-radius: 0.5rem;
}
</style>
