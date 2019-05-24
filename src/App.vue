<template>
  <div style="display: none;">
  </div>
</template>

<script>
import 'leaflet-draw'
import 'leaflet-toolbar'
import ColorPicker from './ColorPicker';
import Draw from './draw';
import Edit from './edit';

export default {
  name: 'l-draw-toolbar',
  props: {
    position: {
      type: String,
      default: 'topright'
    },
  },

  mounted() {
    this.$nextTick(() => {
      const map = this.$parent.$parent.$refs.map.mapObject;

      let editActions = [
        L.Toolbar2.EditAction.Popup.Edit,
        L.Toolbar2.EditAction.Popup.Delete,
        L.Toolbar2.Action.extendOptions({
          toolbarIcon: { 
            className: 'leaflet-color-picker', 
            html: '<i class="fas fa-fill-drip"></i>' 
          },
          subToolbar: new L.Toolbar2({ actions: [
            L.ColorPicker.extendOptions({ color: '#db1d0f' }),
            L.ColorPicker.extendOptions({ color: '#025100' }),
            L.ColorPicker.extendOptions({ color: '#ffff00' }),
            L.ColorPicker.extendOptions({ color: '#0000ff' })
          ]})
        })
      ];

      new L.Toolbar2.DrawToolbar({
          position: this.position
      }).addTo(map);

      map.on('draw:created', function (e) {
        var type = e.layerType,
            layer = e.layer;

        layer.on('click', function(event) {
          this.editMode = true
          new L.Toolbar2.EditToolbar.Popup(event.latlng, {
            actions: editActions
          }).addTo(map, layer);
        });
        
        layer.addTo(map);
      });
    })
  },

}

</script>

<style lang="scss">
@import './../node_modules/leaflet-draw/dist/leaflet.draw.css';
@import './../node_modules/leaflet-toolbar/dist/leaflet.toolbar.css';

.leaflet-draw-toolbar.leaflet-control-toolbar {
  margin-top: 12px;
  margin-top: 12px;
}

// NOTE: This is bad because it makes it impossible to use Leaflet.draw and Leaflet.toolbar on the same page.
.leaflet-draw-toolbar a {
  background-image: none;
  background-repeat: no-repeat;
}

.leaflet-retina .leaflet-draw-toolbar a {
  background-image: none;
  background-size: 300px 30px;
}

.leaflet-draw-toolbar {
  .leaflet-draw-edit-edit,
  .leaflet-draw-edit-remove,
  .leaflet-draw-draw-polygon,
  .leaflet-draw-draw-polyline,
  .leaflet-draw-draw-circle,
  .leaflet-draw-draw-marker,
  .leaflet-draw-draw-rectangle {
    background-image: url("images/spritesheet.png");
    background-repeat: no-repeat;
  }
}

.leaflet-retina {
  .leaflet-draw-toolbar {
    .leaflet-draw-edit-edit,
    .leaflet-draw-edit-remove,
    .leaflet-draw-draw-polygon,
    .leaflet-draw-draw-polyline,
    .leaflet-draw-draw-circle,
    .leaflet-draw-draw-marker,
    .leaflet-draw-draw-rectangle {
      background-image: url("images/spritesheet-2x.png");
      background-size: 300px 30px;
    }
  }
}
</style>