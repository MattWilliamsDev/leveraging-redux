import React, { useCallback, useEffect, useState } from "react";
import { useDispatch, useMappedState } from "redux-react-hook";
import { isArrayLike } from "../../utils/isArrayLike";
import { isObject } from "../../utils/isObject";
import { selectSlice } from "./../../store/selectors";
import { setIsVisible as setIsVisibleAction } from "../../store/Banner/actions";
import { usePrevious } from "../../hooks/usePrevious";

export class Banner extends React.Component {
  renderMessage () {
    const { message } = this.props;
    if (typeof message === "string") {
      return message;
    }
    if (isArrayLike(message)) {
      return message.map((m, index) => <div key={index}>{`${m.code}: ${m.message}`}</div>);
    }
    if (isObject(message)) {
      return !!message.message ? message.message : JSON.stringify(message);
    }
    return message;
  }

  showBanner () {
    this.props.setIsVisible( true );
  }

  hideBanner () {
    this.props.setIsVisible( false );
  }

  render () {
    const { isVisible, message } = this.props;
    return isVisible && (
      <div data-id="banner" className="banner banner--error">
        <div className="banner--row">
          <i data-id="banner-icon" className="banner--icon dashing-icon dashing-icon--white dashing-icon--alert-filled" />
          <h3 className="banner--title" data-id="banner-message">
            {renderMessage()}
          </h3>
        </div>
      </div>
    );
  }
}

const mapStateToProps = ( state ) => ({
  isVisible: state.banner.isVisible,
  message: state.banner.message
});

const mapDispatchToProps = (dispatch) => ({
  setIsVisible: ( visible ) => dispatch( setIsVisibleAction( visible ) ),
});

export default connect(mapStateToProps, mapDispatchToProps)(Banner);



export function Banner() {
  // Select our state "slice". In this case, "banner".
  // This correlates to the entries in `buildRootReducer`
  const mapState = useCallback((state) => state.banner, []); // This is memoized
  const { isVisible, message } = useMappedState(mapState); // Get our state variables via this hook

  function renderMessage() {
    if (typeof message === "string") {
      return message;
    }
    if (isArrayLike(message)) {
      return message.map((m, index) => <div key={index}>{`${m.code}: ${m.message}`}</div>);
    }
    if (isObject(message)) {
      return !!message.message ? message.message : JSON.stringify(message);
    }
    return message;
  }

  return isVisible && (
    <div data-id="banner" className="banner banner--error">
      <div className="banner--row">
        <i data-id="banner-icon" className="banner--icon dashing-icon dashing-icon--white dashing-icon--alert-filled" />
        <h3 className="banner--title" data-id="banner-message">
          {renderMessage()}
        </h3>
      </div>
    </div>
  );
}

export default Banner;
